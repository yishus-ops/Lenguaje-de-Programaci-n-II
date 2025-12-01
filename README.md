using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace Coppel
{
    public partial class Form1 : Form
    {
        private COPPELDataSet datos;

        private COPPELDataSetTableAdapters.EmpleadoTableAdapter empleadoTA;
        private COPPELDataSetTableAdapters.centroTrabajoTableAdapter centroTrabajoTA;
        private COPPELDataSetTableAdapters.puestosTableAdapter puestosTA;
        private COPPELDataSetTableAdapters.DirectivosTableAdapter directivosTA;
        public Form1()
        {
            InitializeComponent();
            datos = new COPPELDataSet();
            empleadoTA = new COPPELDataSetTableAdapters.EmpleadoTableAdapter();
            centroTrabajoTA = new COPPELDataSetTableAdapters.centroTrabajoTableAdapter();
            puestosTA = new COPPELDataSetTableAdapters.puestosTableAdapter();
            directivosTA = new COPPELDataSetTableAdapters.DirectivosTableAdapter();
        }


        private void dataGridView1_cellContentClick(object sender, DataGridViewCellEventArgs e)
        {
            // vacio por que no necesita nada de aqui
        }



        private void Form1_load(object sender, EventArgs e)
        {
            try
            {
                //llenar las tablas desde la base de datos
                empleadoTA.Fill(datos.Empleado);
                centroTrabajoTA.Fill(datos.centroTrabajo);
                puestosTA.Fill(datos.puestos);
                directivosTA.Fill(datos.Directivos);

                //enlazar los DataGridView con las datatable
                dgvempleadoTA.DataSource = datos.Empleado;
                dgvCentroTrabajo.DataSource = datos.centroTrabajo;
                dgvPuestos.DataSource = datos.puestos;
                dgvDirectivos.DataSource = datos.Directivos;
            }
            catch (Exception ex)
            {
                MessageBox.Show(
                    "Error al cargar los datos desde la base de datos:\n" + ex.Message,
                    "Error",
                    MessageBoxButtons.OK,
                    MessageBoxIcon.Error
                    );
            }
        }

        private void Form1_Load_1(object sender, EventArgs e)
        {
            // TODO: esta línea de código carga datos en la tabla 'cOPPELDataSet.Directivos' Puede moverla o quitarla según sea necesario.
            this.directivosTableAdapter.Fill(this.cOPPELDataSet.Directivos);
            // TODO: esta línea de código carga datos en la tabla 'cOPPELDataSet.puestos' Puede moverla o quitarla según sea necesario.
            this.puestosTableAdapter.Fill(this.cOPPELDataSet.puestos);
            // TODO: esta línea de código carga datos en la tabla 'cOPPELDataSet.centroTrabajo' Puede moverla o quitarla según sea necesario.
            this.centroTrabajoTableAdapter.Fill(this.cOPPELDataSet.centroTrabajo);
            // TODO: esta línea de código carga datos en la tabla 'cOPPELDataSet.Empleado' Puede moverla o quitarla según sea necesario.
            this.empleadoTableAdapter.Fill(this.cOPPELDataSet.Empleado);

        }
    }
}
