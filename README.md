import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JPasswordField;
import javax.swing.JTextField;

class t implements ActionListener {

    private static JLabel userlabel;
    private static JLabel passlabel;
    private static JTextField usertext;
    private static JPasswordField passtext;
    private static JButton loginButton;
    private static JButton showHideButton;
    private static JLabel success;
    private static boolean isPasswordVisible = false;

    public static void main(String[] args) {
        JFrame frame = new JFrame();
        JPanel panel = new JPanel();

        frame.setSize(500, 300);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        frame.add(panel);
        panel.setLayout(null);

        userlabel = new JLabel("User");
        userlabel.setBounds(10, 20, 80, 25);
        panel.add(userlabel);

        usertext = new JTextField(20);
        usertext.setBounds(100, 20, 165, 25);
        panel.add(usertext);

        passlabel = new JLabel("Password");
        passlabel.setBounds(10, 50, 80, 25);
        panel.add(passlabel);

        passtext = new JPasswordField();
        passtext.setBounds(100, 50, 165, 25);
        panel.add(passtext);

        loginButton = new JButton("Login");
        loginButton.setBounds(100, 90, 80, 25);
        loginButton.addActionListener(new t());
        panel.add(loginButton);

        showHideButton = new JButton("Show");
        showHideButton.setBounds(270, 50, 80, 25);
        showHideButton.addActionListener(new t());
        panel.add(showHideButton);

        success = new JLabel("");
        success.setBounds(10, 130, 300, 25);
        panel.add(success);

        frame.setVisible(true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        String command = e.getActionCommand();

        if (command.equals("Login")) {
            String user = usertext.getText();
            String password = new String(passtext.getPassword());
            if (user.equals("Alok") && password.equals("abcde")) {
                success.setText("LOGIN SUCCESSFUL!");
            } else {
                success.setText("Wrong password, please try again!");
            }
        } else if (command.equals("Show")) {
            if (isPasswordVisible) {
                passtext.setEchoChar('*');
                showHideButton.setText("Show");
                isPasswordVisible = false;
            } else {
                passtext.setEchoChar((char) 0);
                showHideButton.setText("Hide");
                isPasswordVisible = true;
            }
        }
    }
}
