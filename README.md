package com.mycompany.faktorialgui;
import javax.swing.*;
import java.awt.event.*;
import java.awt.*;

public class FaktorialGUI extends JFrame implements ActionListener {
    private JTextField inputField;
    private JButton hitungButton;
    private JLabel hasilLabel;
    
    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            new FaktorialGUI();
        });
    }


    public FaktorialGUI() {
        setTitle("Faktorial");
        setSize(500, 300);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setLocationRelativeTo(null);
        setResizable(false);

        JPanel panel = new JPanel();
        

        inputField = new JTextField(10);
        inputField.setPreferredSize(new Dimension(100, 30));
        hitungButton = new JButton("Hitung");
        hasilLabel = new JLabel("Hasil:");

        hitungButton.addActionListener(this);

        panel.add(new JLabel("Masukkan bilangan: "));
        panel.add(inputField);
        

        JPanel buttonPanel = new JPanel();
        buttonPanel.add(hitungButton);
        panel.add(buttonPanel);

        panel.add(hasilLabel);

        add(panel);
        setVisible(true);
    }

    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == hitungButton) {
            try {
                int bilangan = Integer.parseInt(inputField.getText());

                if (bilangan < 0) {
                    JOptionPane.showMessageDialog(this, "Masukkan bilangan positif!");
                    return;
                }

                long hasil = hitungFaktorial(bilangan);
                hasilLabel.setText("Hasil: " + hasil);
            } catch (NumberFormatException ex) {
                JOptionPane.showMessageDialog(this, "Masukkan bilangan yang valid!");
            }
        }
    }

    private long hitungFaktorial(int n) {
        if (n == 0 || n == 1) {
            return 1;
        }

        long faktorial = 1;
        for (int i = 2; i <= n; i++) {
            faktorial *= i;
        }
        return faktorial;
    }

    
    private void setResizeable(boolean b) {
        throw new UnsupportedOperationException("Not supported yet."); 
    }
}