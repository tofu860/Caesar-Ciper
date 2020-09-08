# Caesar-Ciper
Caesar Ciper

using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Drawing.Text;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace CaesarCiperEncryption
{
    public partial class CaesarCiper : Form
    {
        public CaesarCiper()
        {
            InitializeComponent();
        }

        private void label1_Click(object sender, EventArgs e)
        {

        }

        private void label2_Click(object sender, EventArgs e)
        {

        }

        private void textBox2_TextChanged(object sender, EventArgs e)
        {

        }

        private void Form1_Load(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {
            string origMessage = normalText.Text;
            int shiftNum = Int32.Parse(textBox3.Text);

            cypherText.Text = doEncryption(origMessage.ToLower(), shiftNum);


        }
        private static string doEncryption(string words, int shiftNo)
        {
            char[] buffer = words.ToCharArray();

            for (int i = 0; i < buffer.Length; i++)
            {
                // each letter will be seperated and then changed.

                char letter = buffer[i];
                // shift the letters according to the shift no variable

                letter = (char)(letter + shiftNo);
                // Subtract 26 on overflow
                // Add 26 on overflow 

                if (letter > 'z')
                {
                    letter = (char)(letter - 26);
                }
                else if (letter < 'a')
                {
                    letter = (char)(letter + 26);
                }
                //Store

                buffer[i] = letter;
            }

            return new string(buffer);

        }
        private void helpToolStripMenuItem_Click(object sender, EventArgs e)
        {
            helpScreen helpForm = new helpScreen();

            helpForm.Show();
        }

        private void button3_Click(object sender, EventArgs e)
        {
            this.Close();
        }

        private void button2_Click(object sender, EventArgs e)
        {
            //string words = "vjku<ycu<eqttgevna<gpetarvgf";
            int shiftNum = Int32.Parse(textBox3.Text);


            normalText.Text = DoDecryption(cypherText.Text.ToUpper(), shiftNum);


        }
        public string DoDecryption(string words, int shiftNo)
        {

            char[] buffer = words.ToCharArray();

            for (int i = 0; i < buffer.Length; i++)
            {
                // each letter will be seperated and then changed.

                char letter = buffer[i];
                // shift the letters according to the shift no variable

                letter = (char)(letter - shiftNo);
                // Subtract 26 on overflow
                // Add 26 on overflow 

                if (letter > 'z')
                {
                    letter = (char)(letter - 26);
                }
                else if (letter < 'a')
                {
                    letter = (char)(letter + 26);
                }
                //Store

                buffer[i] = letter;
            }

            return new string(buffer);
        }



        private void encryptToolStripMenuItem_Click(object sender, EventArgs e)
        {

        }
    }
}

