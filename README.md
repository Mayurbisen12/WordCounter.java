# WordCounter.java
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class WordCounter extends JFrame {

    private JTextArea textArea;
    private JButton countButton;
    private JLabel wordCountLabel;

    public WordCounter() {
        super("Word Counter");
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setLayout(new BorderLayout());

        // Text Area
        textArea = new JTextArea(10, 20);
        add(new JScrollPane(textArea), BorderLayout.CENTER);

        // Button Panel
        JPanel buttonPanel = new JPanel();
        countButton = new JButton("Count Words");
        countButton.addActionListener(new ActionListener() {
           public void actionPerformed(ActionEvent e) {
                countWords();
            }
        });
        buttonPanel.add(countButton);
        add(buttonPanel, BorderLayout.SOUTH);

        // Word Count Label
        wordCountLabel = new JLabel("Word Count: 0");
        add(wordCountLabel, BorderLayout.NORTH);

        pack();
        setVisible(true);
    }

    private void countWords() {
        String text = textArea.getText();
        String[] words = text.split("\\s+");
        int wordCount = words.length;
        wordCountLabel.setText("Word Count: " + wordCount);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                new WordCounter();
            }
        });
    }
}

