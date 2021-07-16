# Limpar-Memoria-C#
 public class FerramentasMemoria
    {
        [DllImport("Kernel32.dll", EntryPoint = "SetProcessWorkingSetSize", SetLastError = true, CallingConvention = CallingConvention.StdCall)]
        
        internal static extern bool SetProcessWorkingSetSize(IntPtr pProcess, int dwMinimunWorkingSetSize, int dwMaximumWorkingSetSize);

        public static void limpaMemoria()
        {
            //Nome do Processo
            System.Diagnostics.Process[] proc = System.Diagnostics.Process.GetProcessesByName("nomeprocesso");

            // Passar o Handle
            IntPtr pHandle = proc[0].Handle;

            //Limpar a memoria
            SetProcessWorkingSetSize(pHandle, -1, -1);
        }
    }
    
    public partial class Form1 : Form
    {

           public Form1() {  InitializeComponent(); }
     
          /* Chamar o metodo */
          FerramentasMemoria.limpaMemoria();
    }
