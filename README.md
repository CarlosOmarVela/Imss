# Imss
comparar

/*
               File: IMSSOfflineDatabase
        Description: IMSSOffline Database
             Author: GeneXus Java Generator version 10_3_4-93925
       Generated on: September 25, 2015 13:49:16.70
       Program type: Callable routine
          Main DBMS: postgresql
*/
package com.imss ;
import com.imss.*;
import com.genexus.*;
import com.genexus.ui.*;
import com.genexus.db.*;
import com.genexus.distributed.*;
import com.genexus.uifactory.*;
import com.genexus.search.*;
import java.sql.*;

public final  class imssofflinedatabase extends GXProcedure
{
   public imssofflinedatabase( int remoteHandle )
   {
      super( remoteHandle , new ModelContext( imssofflinedatabase.class ), "" );
   }

   public imssofflinedatabase( int remoteHandle ,
                               ModelContext context )
   {
      super( remoteHandle , context, "" );
   }

   public void execute( )
   {
      execute_int();
   }

   private void execute_int( )
   {
   }

   protected void GXStart( )
   {
      /* Execute user event: e11052 */
      e11052 ();
      if ( returnInSub )
      {
         returnInSub = true;
         cleanup();
         if (true) return;
      }
   }

   public void e11052( )
   {
      /* Start Routine */
      GXt_char1 = AV4Matricula ;
      GXv_char2[0] = GXt_char1 ;
      new com.imss.getmatriculamedico(remoteHandle, context).execute( GXv_char2) ;
      imssofflinedatabase.this.GXt_char1 = GXv_char2[0] ;
      AV4Matricula = GXt_char1 ;
      AV4Matricula = GXutil.trim( AV4Matricula) ;
      GXt_char1 = AV5UserMedico ;
      GXv_char2[0] = GXt_char1 ;
      new com.imss.obtenerlogin(remoteHandle, context).execute( GXv_char2) ;
      imssofflinedatabase.this.GXt_char1 = GXv_char2[0] ;
      AV5UserMedico = GXt_char1 ;
      GXt_objcol_int3 = AV2ColDFFormInstId ;
      GXv_objcol_int4[0] = GXt_objcol_int3 ;
      new com.imss.obtenercoldfforminstiddelospacientes(remoteHandle, context).execute( GXv_objcol_int4) ;
      GXt_objcol_int3 = GXv_objcol_int4[0] ;
      AV2ColDFFormInstId = GXt_objcol_int3 ;
      GXt_objcol_int3 = AV3ColPacienteNSSAgregado ;
      GXv_objcol_int4[0] = GXt_objcol_int3 ;
      new com.imss.obtenercolpacientenssagregado(remoteHandle, context).execute( GXv_objcol_int4) ;
      GXt_objcol_int3 = GXv_objcol_int4[0] ;
      AV3ColPacienteNSSAgregado = GXt_objcol_int3 ;
   }

   /*  Synchronize for table (Full)  Medico */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtMedico( )
   {
      /* Begin Synchronize  Medico */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("Medico");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN2 */
      pr_default.execute(0, new Object[] {AV5UserMedico});
      while ( (pr_default.getStatus(0) != 101) )
      {
         A312MedicoDebeMostarTerm = IMSSOFFLIN2_A312MedicoDebeMostarTerm[0] ;
         A302MedicoDebeValidarDatos = IMSSOFFLIN2_A302MedicoDebeValidarDatos[0] ;
         A300MedicoUltimaActualizacion = IMSSOFFLIN2_A300MedicoUltimaActualizacion[0] ;
         A297MedicoMatricula = IMSSOFFLIN2_A297MedicoMatricula[0] ;
         n297MedicoMatricula = IMSSOFFLIN2_n297MedicoMatricula[0] ;
         A296MedicoApellidoMaterno = IMSSOFFLIN2_A296MedicoApellidoMaterno[0] ;
         A295MedicoApellidoPaterno = IMSSOFFLIN2_A295MedicoApellidoPaterno[0] ;
         A294MedicoSegundoNombre = IMSSOFFLIN2_A294MedicoSegundoNombre[0] ;
         A293MedicoPrimerNombre = IMSSOFFLIN2_A293MedicoPrimerNombre[0] ;
         A292UserMedico = IMSSOFFLIN2_A292UserMedico[0] ;
         gxsyncline.add(GXutil.rtrim( A296MedicoApellidoMaterno));
         gxsyncline.add(GXutil.rtrim( A295MedicoApellidoPaterno));
         gxsyncline.add(GXutil.booltostr( A312MedicoDebeMostarTerm));
         gxsyncline.add(GXutil.booltostr( A302MedicoDebeValidarDatos));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A297MedicoMatricula, (byte)(10), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A293MedicoPrimerNombre));
         gxsyncline.add(GXutil.rtrim( A294MedicoSegundoNombre));
         gxsyncline.add(GXutil.timeToCharREST( A300MedicoUltimaActualizacion));
         gxsyncline.add(GXutil.rtrim( A292UserMedico));
         gxsynchashkey.add(GXutil.rtrim( A292UserMedico));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         /* Exiting from a For First loop. */
         if (true) break;
      }
      pr_default.close(0);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable5[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable7[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "Medico" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable5 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable7 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  PacienteMedicoOffline */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtPacienteMedicoOffline( )
   {
      /* Begin Synchronize  PacienteMedicoOffline */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("PacienteMedicoOffline");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      pr_default.dynParam(1, new Object[]{ new Object[]{
                                           A75PacienteNSSAgregado ,
                                           AV3ColPacienteNSSAgregado ,
                                           A81Matricula ,
                                           AV4Matricula },
                                           new int[] {
                                           TypeConstants.STRING, TypeConstants.OBJECT_COLLECTION, TypeConstants.STRING, TypeConstants.STRING
                                           }
      });
      /* Using cursor IMSSOFFLIN3 */
      pr_default.execute(1, new Object[] {AV4Matricula});
      while ( (pr_default.getStatus(1) != 101) )
      {
         A75PacienteNSSAgregado = IMSSOFFLIN3_A75PacienteNSSAgregado[0] ;
         A81Matricula = IMSSOFFLIN3_A81Matricula[0] ;
         A3PacienteAgregado = IMSSOFFLIN3_A3PacienteAgregado[0] ;
         A2PacienteNSS = IMSSOFFLIN3_A2PacienteNSS[0] ;
         A75PacienteNSSAgregado = IMSSOFFLIN3_A75PacienteNSSAgregado[0] ;
         gxsyncline.add(GXutil.rtrim( A81Matricula));
         gxsynchashkey.add(GXutil.rtrim( A81Matricula));
         gxsyncline.add(GXutil.rtrim( A3PacienteAgregado));
         gxsynchashkey.add(GXutil.rtrim( A3PacienteAgregado));
         gxsyncline.add(GXutil.rtrim( A2PacienteNSS));
         gxsynchashkey.add(GXutil.rtrim( A2PacienteNSS));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(1);
      }
      pr_default.close(1);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "PacienteMedicoOffline" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  CIE10 */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtCIE10( )
   {
      /* Begin Synchronize  CIE10 */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("CIE10");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN4 */
      pr_default.execute(2);
      while ( (pr_default.getStatus(2) != 101) )
      {
         A69CIECodigo = IMSSOFFLIN4_A69CIECodigo[0] ;
         A10CIE10Descripcion = IMSSOFFLIN4_A10CIE10Descripcion[0] ;
         A1CIE10Id = IMSSOFFLIN4_A1CIE10Id[0] ;
         gxsyncline.add(A10CIE10Descripcion);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(A69CIECodigo);
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(2);
      }
      pr_default.close(2);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "CIE10" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  ExpedienteDiagnostico */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtExpedienteDiagnostico( )
   {
      /* Begin Synchronize  ExpedienteDiagnostico */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("ExpedienteDiagnostico");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      pr_default.dynParam(3, new Object[]{ new Object[]{
                                           A75PacienteNSSAgregado ,
                                           AV3ColPacienteNSSAgregado },
                                           new int[] {
                                           TypeConstants.STRING, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN5 */
      pr_default.execute(3);
      while ( (pr_default.getStatus(3) != 101) )
      {
         A75PacienteNSSAgregado = IMSSOFFLIN5_A75PacienteNSSAgregado[0] ;
         A34MMatricula = IMSSOFFLIN5_A34MMatricula[0] ;
         n34MMatricula = IMSSOFFLIN5_n34MMatricula[0] ;
         A33MApMat = IMSSOFFLIN5_A33MApMat[0] ;
         n33MApMat = IMSSOFFLIN5_n33MApMat[0] ;
         A32MApPat = IMSSOFFLIN5_A32MApPat[0] ;
         n32MApPat = IMSSOFFLIN5_n32MApPat[0] ;
         A31MNombre = IMSSOFFLIN5_A31MNombre[0] ;
         n31MNombre = IMSSOFFLIN5_n31MNombre[0] ;
         A30MBMatricula = IMSSOFFLIN5_A30MBMatricula[0] ;
         n30MBMatricula = IMSSOFFLIN5_n30MBMatricula[0] ;
         A29MBApMat = IMSSOFFLIN5_A29MBApMat[0] ;
         n29MBApMat = IMSSOFFLIN5_n29MBApMat[0] ;
         A28MBApPat = IMSSOFFLIN5_A28MBApPat[0] ;
         n28MBApPat = IMSSOFFLIN5_n28MBApPat[0] ;
         A27MBNombre = IMSSOFFLIN5_A27MBNombre[0] ;
         n27MBNombre = IMSSOFFLIN5_n27MBNombre[0] ;
         A26JSMatricula = IMSSOFFLIN5_A26JSMatricula[0] ;
         n26JSMatricula = IMSSOFFLIN5_n26JSMatricula[0] ;
         A25JSApMat = IMSSOFFLIN5_A25JSApMat[0] ;
         n25JSApMat = IMSSOFFLIN5_n25JSApMat[0] ;
         A24JSApPat = IMSSOFFLIN5_A24JSApPat[0] ;
         n24JSApPat = IMSSOFFLIN5_n24JSApPat[0] ;
         A23JSNombre = IMSSOFFLIN5_A23JSNombre[0] ;
         n23JSNombre = IMSSOFFLIN5_n23JSNombre[0] ;
         A22DiagnosticoCirugiaFecha = IMSSOFFLIN5_A22DiagnosticoCirugiaFecha[0] ;
         n22DiagnosticoCirugiaFecha = IMSSOFFLIN5_n22DiagnosticoCirugiaFecha[0] ;
         A21DiagnosticoCirugia = IMSSOFFLIN5_A21DiagnosticoCirugia[0] ;
         n21DiagnosticoCirugia = IMSSOFFLIN5_n21DiagnosticoCirugia[0] ;
         A20Cama = IMSSOFFLIN5_A20Cama[0] ;
         n20Cama = IMSSOFFLIN5_n20Cama[0] ;
         A6ServicioId = IMSSOFFLIN5_A6ServicioId[0] ;
         A19DiagnosticoResumen = IMSSOFFLIN5_A19DiagnosticoResumen[0] ;
         n19DiagnosticoResumen = IMSSOFFLIN5_n19DiagnosticoResumen[0] ;
         A18DiagnosticoComplemento = IMSSOFFLIN5_A18DiagnosticoComplemento[0] ;
         n18DiagnosticoComplemento = IMSSOFFLIN5_n18DiagnosticoComplemento[0] ;
         A35DiagnosticoFechaAlta = IMSSOFFLIN5_A35DiagnosticoFechaAlta[0] ;
         n35DiagnosticoFechaAlta = IMSSOFFLIN5_n35DiagnosticoFechaAlta[0] ;
         A17DiagnosticoFechaIngreso = IMSSOFFLIN5_A17DiagnosticoFechaIngreso[0] ;
         n17DiagnosticoFechaIngreso = IMSSOFFLIN5_n17DiagnosticoFechaIngreso[0] ;
         A1CIE10Id = IMSSOFFLIN5_A1CIE10Id[0] ;
         A3PacienteAgregado = IMSSOFFLIN5_A3PacienteAgregado[0] ;
         A2PacienteNSS = IMSSOFFLIN5_A2PacienteNSS[0] ;
         A75PacienteNSSAgregado = IMSSOFFLIN5_A75PacienteNSSAgregado[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A20Cama));
         gxsyncline.add(A21DiagnosticoCirugia);
         gxsyncline.add(GXutil.timeToCharREST( A22DiagnosticoCirugiaFecha));
         gxsyncline.add(A18DiagnosticoComplemento);
         gxsyncline.add(GXutil.timeToCharREST( A35DiagnosticoFechaAlta));
         gxsyncline.add(GXutil.dateToCharREST( A17DiagnosticoFechaIngreso));
         gxsyncline.add(A19DiagnosticoResumen);
         gxsyncline.add(GXutil.rtrim( A25JSApMat));
         gxsyncline.add(GXutil.rtrim( A24JSApPat));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A26JSMatricula, (byte)(10), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A23JSNombre));
         gxsyncline.add(GXutil.rtrim( A33MApMat));
         gxsyncline.add(GXutil.rtrim( A32MApPat));
         gxsyncline.add(GXutil.rtrim( A29MBApMat));
         gxsyncline.add(GXutil.rtrim( A28MBApPat));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A30MBMatricula, (byte)(10), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A27MBNombre));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A34MMatricula, (byte)(10), (byte)(0), ".", "")));
         gxsyncline.add(A31MNombre);
         gxsyncline.add(GXutil.rtrim( A3PacienteAgregado));
         gxsynchashkey.add(GXutil.rtrim( A3PacienteAgregado));
         gxsyncline.add(GXutil.rtrim( A2PacienteNSS));
         gxsynchashkey.add(GXutil.rtrim( A2PacienteNSS));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A6ServicioId, (byte)(4), (byte)(0), ".", "")));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(3);
      }
      pr_default.close(3);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "ExpedienteDiagnostico" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  Texto */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtTexto( )
   {
      /* Begin Synchronize  Texto */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("Texto");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN6 */
      pr_default.execute(4);
      while ( (pr_default.getStatus(4) != 101) )
      {
         A323nada = IMSSOFFLIN6_A323nada[0] ;
         A311TextoDescripcion = IMSSOFFLIN6_A311TextoDescripcion[0] ;
         A310TextoTitulo = IMSSOFFLIN6_A310TextoTitulo[0] ;
         A309TextoId = IMSSOFFLIN6_A309TextoId[0] ;
         gxsyncline.add(A311TextoDescripcion);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A309TextoId, (byte)(4), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A309TextoId, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add(A310TextoTitulo);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A323nada, (byte)(4), (byte)(0), ".", "")));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(4);
      }
      pr_default.close(4);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "Texto" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  DFParm */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtDFParm( )
   {
      /* Begin Synchronize  DFParm */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("DFParm");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN7 */
      pr_default.execute(5);
      while ( (pr_default.getStatus(5) != 101) )
      {
         A169DFParmIsMetaData = IMSSOFFLIN7_A169DFParmIsMetaData[0] ;
         A168DFParmVal = IMSSOFFLIN7_A168DFParmVal[0] ;
         A167DFParmName = IMSSOFFLIN7_A167DFParmName[0] ;
         A102DFParmId = IMSSOFFLIN7_A102DFParmId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A102DFParmId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A102DFParmId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.booltostr( A169DFParmIsMetaData));
         gxsyncline.add(GXutil.rtrim( A167DFParmName));
         gxsyncline.add(GXutil.rtrim( A168DFParmVal));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(5);
      }
      pr_default.close(5);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "DFParm" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  DXAuxImagen */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtDXAuxImagen( )
   {
      /* Begin Synchronize  DXAuxImagen */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("DXAuxImagen");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      pr_default.dynParam(6, new Object[]{ new Object[]{
                                           A75PacienteNSSAgregado ,
                                           AV3ColPacienteNSSAgregado },
                                           new int[] {
                                           TypeConstants.STRING, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN8 */
      pr_default.execute(6);
      while ( (pr_default.getStatus(6) != 101) )
      {
         A75PacienteNSSAgregado = IMSSOFFLIN8_A75PacienteNSSAgregado[0] ;
         A40000DXAuxImagenImg_GXI = IMSSOFFLIN8_A40000DXAuxImagenImg_GXI[0] ;
         A322DXAuxImagenExtension = IMSSOFFLIN8_A322DXAuxImagenExtension[0] ;
         A73DXAuxImagenNombre = IMSSOFFLIN8_A73DXAuxImagenNombre[0] ;
         A16DXAuxImagenUserAlta = IMSSOFFLIN8_A16DXAuxImagenUserAlta[0] ;
         A15DXAuxImagenFechaAlta = IMSSOFFLIN8_A15DXAuxImagenFechaAlta[0] ;
         A14DXAuxImagenImg = IMSSOFFLIN8_A14DXAuxImagenImg[0] ;
         A5DXAuxImagenId = IMSSOFFLIN8_A5DXAuxImagenId[0] ;
         A1CIE10Id = IMSSOFFLIN8_A1CIE10Id[0] ;
         A3PacienteAgregado = IMSSOFFLIN8_A3PacienteAgregado[0] ;
         A2PacienteNSS = IMSSOFFLIN8_A2PacienteNSS[0] ;
         A75PacienteNSSAgregado = IMSSOFFLIN8_A75PacienteNSSAgregado[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A322DXAuxImagenExtension));
         gxsyncline.add(GXutil.timeToCharREST( A15DXAuxImagenFechaAlta));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A5DXAuxImagenId, (byte)(4), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A5DXAuxImagenId, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add((!(GXutil.strcmp("", A40000DXAuxImagenImg_GXI)==0) ? GXutil.getRelativeBlobFile( A40000DXAuxImagenImg_GXI) : GXutil.rtrim( A14DXAuxImagenImg)));
         gxsyncline.add(A40000DXAuxImagenImg_GXI);
         gxsyncline.add(GXutil.rtrim( A73DXAuxImagenNombre));
         gxsyncline.add(GXutil.rtrim( A16DXAuxImagenUserAlta));
         gxsyncline.add(GXutil.rtrim( A3PacienteAgregado));
         gxsynchashkey.add(GXutil.rtrim( A3PacienteAgregado));
         gxsyncline.add(GXutil.rtrim( A2PacienteNSS));
         gxsynchashkey.add(GXutil.rtrim( A2PacienteNSS));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(6);
      }
      pr_default.close(6);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "DXAuxImagen" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  DXAuxDocto */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtDXAuxDocto( )
   {
      /* Begin Synchronize  DXAuxDocto */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("DXAuxDocto");
      gxsyncresponse.add(gxsyncheader);
	  gxsyncresponse_hash = new com.genexus.GxUnknownObjectCollection();
	  gxsyncresponse_hash.add(gxsyncheader);	  
      gxsyncline = new com.genexus.internet.StringCollection() ;
	  gxsyncline_hash = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      pr_default.dynParam(7, new Object[]{ new Object[]{
                                           A75PacienteNSSAgregado ,
                                           AV3ColPacienteNSSAgregado },
                                           new int[] {
                                           TypeConstants.STRING, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN9 */
      pr_default.execute(7);
      while ( (pr_default.getStatus(7) != 101) )
      {
         A75PacienteNSSAgregado = IMSSOFFLIN9_A75PacienteNSSAgregado[0] ;
         A74DXAuxDoctoNombre = IMSSOFFLIN9_A74DXAuxDoctoNombre[0] ;
         A82DXAuxDoctoExtension = IMSSOFFLIN9_A82DXAuxDoctoExtension[0] ;
         A13DXAuxDoctoUserAlta = IMSSOFFLIN9_A13DXAuxDoctoUserAlta[0] ;
         A12DXAuxDoctoFechaAlta = IMSSOFFLIN9_A12DXAuxDoctoFechaAlta[0] ;
         A11DXAuxDoctoDocumento = IMSSOFFLIN9_A11DXAuxDoctoDocumento[0] ;
         A4DXAuxDoctoId = IMSSOFFLIN9_A4DXAuxDoctoId[0] ;
         A1CIE10Id = IMSSOFFLIN9_A1CIE10Id[0] ;
         A3PacienteAgregado = IMSSOFFLIN9_A3PacienteAgregado[0] ;
         A2PacienteNSS = IMSSOFFLIN9_A2PacienteNSS[0] ;
         A75PacienteNSSAgregado = IMSSOFFLIN9_A75PacienteNSSAgregado[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
		 gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
         
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.getRelativeBlobFile( A11DXAuxDoctoDocumento));
		 //gxsyncline_hash path de Blobs no se agregan a la sincronizacion
         
         gxsyncline.add(GXutil.rtrim( A82DXAuxDoctoExtension));
		 gxsyncline_hash.add(GXutil.rtrim( A82DXAuxDoctoExtension));
         
         gxsyncline.add(GXutil.timeToCharREST( A12DXAuxDoctoFechaAlta));
		 gxsyncline_hash.add(GXutil.timeToCharREST( A12DXAuxDoctoFechaAlta));
         
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A4DXAuxDoctoId, (byte)(4), (byte)(0), ".", "")));
		 gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A4DXAuxDoctoId, (byte)(4), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A4DXAuxDoctoId, (byte)(4), (byte)(0), ".", "")));
		 
         gxsyncline.add(GXutil.rtrim( A74DXAuxDoctoNombre));
		 gxsyncline_hash.add(GXutil.rtrim( A74DXAuxDoctoNombre));
		 
         gxsyncline.add(GXutil.rtrim( A13DXAuxDoctoUserAlta));
		 gxsyncline_hash.add(GXutil.rtrim( A13DXAuxDoctoUserAlta));
		 
         gxsyncline.add(GXutil.rtrim( A3PacienteAgregado));
		 gxsyncline_hash.add(GXutil.rtrim( A3PacienteAgregado));
         gxsynchashkey.add(GXutil.rtrim( A3PacienteAgregado));
		 
         gxsyncline.add(GXutil.rtrim( A2PacienteNSS));
		 gxsyncline_hash.add(GXutil.rtrim( A2PacienteNSS));
         gxsynchashkey.add(GXutil.rtrim( A2PacienteNSS));
		 
         //gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
		 gxlinehash = GXutil.getMD5Hash( gxsyncline_hash.ToJavascriptSource()) ;
		 
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
		 gxsyncresponse_hash.add(gxsyncline_hash);
         gxsyncline = new com.genexus.internet.StringCollection() ;
		 gxsyncline_hash = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(7);
      }
      pr_default.close(7);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      // gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;	  
	  gxtablecurrenthash = GXutil.getMD5Hash( gxsyncresponse_hash.toJSonString(false)) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "DXAuxDocto" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  Paciente */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtPaciente( )
   {
      /* Begin Synchronize  Paciente */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("Paciente");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      pr_default.dynParam(8, new Object[]{ new Object[]{
                                           A75PacienteNSSAgregado ,
                                           AV3ColPacienteNSSAgregado },
                                           new int[] {
                                           TypeConstants.STRING, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN10 */
      pr_default.execute(8);
      while ( (pr_default.getStatus(8) != 101) )
      {
         A321PacienteServicioId = IMSSOFFLIN10_A321PacienteServicioId[0] ;
         A298PacienteDiagnosticoPhone = IMSSOFFLIN10_A298PacienteDiagnosticoPhone[0] ;
         A291PacienteCie10Id = IMSSOFFLIN10_A291PacienteCie10Id[0] ;
         A76PAcienteFechaIngreso = IMSSOFFLIN10_A76PAcienteFechaIngreso[0] ;
         A75PacienteNSSAgregado = IMSSOFFLIN10_A75PacienteNSSAgregado[0] ;
         A72PacienteCama = IMSSOFFLIN10_A72PacienteCama[0] ;
         A71PacienteDiagnosticoResumido = IMSSOFFLIN10_A71PacienteDiagnosticoResumido[0] ;
         A70PacienteDiagnostico = IMSSOFFLIN10_A70PacienteDiagnostico[0] ;
         A68PacienteFechaNacimiento = IMSSOFFLIN10_A68PacienteFechaNacimiento[0] ;
         A55PacienteNombreCompleto = IMSSOFFLIN10_A55PacienteNombreCompleto[0] ;
         A54PacienteReferencia = IMSSOFFLIN10_A54PacienteReferencia[0] ;
         n54PacienteReferencia = IMSSOFFLIN10_n54PacienteReferencia[0] ;
         A53PacienteFamiliar = IMSSOFFLIN10_A53PacienteFamiliar[0] ;
         n53PacienteFamiliar = IMSSOFFLIN10_n53PacienteFamiliar[0] ;
         A52PacienteTelefono = IMSSOFFLIN10_A52PacienteTelefono[0] ;
         n52PacienteTelefono = IMSSOFFLIN10_n52PacienteTelefono[0] ;
         A51PacienteGenero = IMSSOFFLIN10_A51PacienteGenero[0] ;
         n51PacienteGenero = IMSSOFFLIN10_n51PacienteGenero[0] ;
         A50PacienteEdad = IMSSOFFLIN10_A50PacienteEdad[0] ;
         A46PacienteApMat = IMSSOFFLIN10_A46PacienteApMat[0] ;
         n46PacienteApMat = IMSSOFFLIN10_n46PacienteApMat[0] ;
         A45PacienteApPat = IMSSOFFLIN10_A45PacienteApPat[0] ;
         A44PacienteNombre = IMSSOFFLIN10_A44PacienteNombre[0] ;
         A3PacienteAgregado = IMSSOFFLIN10_A3PacienteAgregado[0] ;
         A2PacienteNSS = IMSSOFFLIN10_A2PacienteNSS[0] ;
         gxsyncline.add(GXutil.dateToCharREST( A76PAcienteFechaIngreso));
         gxsyncline.add(GXutil.rtrim( A3PacienteAgregado));
         gxsynchashkey.add(GXutil.rtrim( A3PacienteAgregado));
         gxsyncline.add(GXutil.rtrim( A46PacienteApMat));
         gxsyncline.add(GXutil.rtrim( A45PacienteApPat));
         gxsyncline.add(GXutil.rtrim( A72PacienteCama));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A291PacienteCie10Id, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(A70PacienteDiagnostico);
         gxsyncline.add(A298PacienteDiagnosticoPhone);
         gxsyncline.add(A71PacienteDiagnosticoResumido);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A50PacienteEdad, (byte)(3), (byte)(0), ".", "")));
         gxsyncline.add(A53PacienteFamiliar);
         gxsyncline.add(GXutil.dateToCharREST( A68PacienteFechaNacimiento));
         gxsyncline.add(GXutil.rtrim( A51PacienteGenero));
         gxsyncline.add(GXutil.rtrim( A2PacienteNSS));
         gxsynchashkey.add(GXutil.rtrim( A2PacienteNSS));
         gxsyncline.add(A75PacienteNSSAgregado);
         gxsyncline.add(GXutil.rtrim( A44PacienteNombre));
         gxsyncline.add(GXutil.rtrim( A55PacienteNombreCompleto));
         gxsyncline.add(GXutil.rtrim( A54PacienteReferencia));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A321PacienteServicioId, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A52PacienteTelefono));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(8);
      }
      pr_default.close(8);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "Paciente" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  DFForm */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtDFForm( )
   {
      /* Begin Synchronize  DFForm */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("DFForm");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN11 */
      pr_default.execute(9);
      while ( (pr_default.getStatus(9) != 101) )
      {
         A317DFFormDsc = IMSSOFFLIN11_A317DFFormDsc[0] ;
         A303DFFormIsSD = IMSSOFFLIN11_A303DFFormIsSD[0] ;
         A159DFFormRunDLT = IMSSOFFLIN11_A159DFFormRunDLT[0] ;
         A236DFFormHelpURL = IMSSOFFLIN11_A236DFFormHelpURL[0] ;
         A176DFFormPrefix = IMSSOFFLIN11_A176DFFormPrefix[0] ;
         A235DFFormPmtHgh = IMSSOFFLIN11_A235DFFormPmtHgh[0] ;
         n235DFFormPmtHgh = IMSSOFFLIN11_n235DFFormPmtHgh[0] ;
         A234DFFormPmtWth = IMSSOFFLIN11_A234DFFormPmtWth[0] ;
         n234DFFormPmtWth = IMSSOFFLIN11_n234DFFormPmtWth[0] ;
         A237DFFormAct = IMSSOFFLIN11_A237DFFormAct[0] ;
         A171DFFormName = IMSSOFFLIN11_A171DFFormName[0] ;
         A115DFFormGuid = IMSSOFFLIN11_A115DFFormGuid[0] ;
         A87DFFormVer = IMSSOFFLIN11_A87DFFormVer[0] ;
         A86DFFormId = IMSSOFFLIN11_A86DFFormId[0] ;
         gxsyncline.add(GXutil.booltostr( A237DFFormAct));
         gxsyncline.add(A317DFFormDsc);
         gxsyncline.add(A115DFFormGuid.toString());
         gxsyncline.add(A236DFFormHelpURL);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A86DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A86DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.booltostr( A303DFFormIsSD));
         gxsyncline.add(GXutil.rtrim( A171DFFormName));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A235DFFormPmtHgh, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A234DFFormPmtWth, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(A176DFFormPrefix);
         gxsyncline.add(GXutil.booltostr( A159DFFormRunDLT));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A87DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A87DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(9);
      }
      pr_default.close(9);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "DFForm" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  FormatoPaciente */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtFormatoPaciente( )
   {
      /* Begin Synchronize  FormatoPaciente */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("FormatoPaciente");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      pr_default.dynParam(10, new Object[]{ new Object[]{
                                           new Long(A90DFFormInstId) ,
                                           AV2ColDFFormInstId },
                                           new int[] {
                                           TypeConstants.LONG, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN12 */
      pr_default.execute(10);
      while ( (pr_default.getStatus(10) != 101) )
      {
         A85FormatoPacienteMedicoNombre = IMSSOFFLIN12_A85FormatoPacienteMedicoNombre[0] ;
         A84FormatoPacienteMedicoMatricula = IMSSOFFLIN12_A84FormatoPacienteMedicoMatricula[0] ;
         A90DFFormInstId = IMSSOFFLIN12_A90DFFormInstId[0] ;
         A80FormatoPacienteAgregado = IMSSOFFLIN12_A80FormatoPacienteAgregado[0] ;
         A79FormatoPacienteNSS = IMSSOFFLIN12_A79FormatoPacienteNSS[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A90DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A90DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A80FormatoPacienteAgregado));
         gxsynchashkey.add(GXutil.rtrim( A80FormatoPacienteAgregado));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A84FormatoPacienteMedicoMatricula, (byte)(10), (byte)(0), ".", "")));
         gxsyncline.add(A85FormatoPacienteMedicoNombre);
         gxsyncline.add(GXutil.rtrim( A79FormatoPacienteNSS));
         gxsynchashkey.add(GXutil.rtrim( A79FormatoPacienteNSS));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(10);
      }
      pr_default.close(10);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "FormatoPaciente" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  Extension */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtExtension( )
   {
      /* Begin Synchronize  Extension */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("Extension");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN13 */
      pr_default.execute(11);
      while ( (pr_default.getStatus(11) != 101) )
      {
         A306ExtensionNombre = IMSSOFFLIN13_A306ExtensionNombre[0] ;
         A305ExtensionTipo = IMSSOFFLIN13_A305ExtensionTipo[0] ;
         A304ExtensionId = IMSSOFFLIN13_A304ExtensionId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A304ExtensionId, (byte)(4), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A304ExtensionId, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A306ExtensionNombre));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A305ExtensionTipo, (byte)(4), (byte)(0), ".", "")));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(11);
      }
      pr_default.close(11);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "Extension" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  DFElemForm */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtDFElemForm( )
   {
      /* Begin Synchronize  DFElemForm */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("DFElemForm");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN14 */
      pr_default.execute(12);
      while ( (pr_default.getStatus(12) != 101) )
      {
         A313DFElemFormReq = IMSSOFFLIN14_A313DFElemFormReq[0] ;
         A316DFElemFormPrtPic = IMSSOFFLIN14_A316DFElemFormPrtPic[0] ;
         A307DFElemFormLoadRule = IMSSOFFLIN14_A307DFElemFormLoadRule[0] ;
         n307DFElemFormLoadRule = IMSSOFFLIN14_n307DFElemFormLoadRule[0] ;
         A266DFElemFormMetadata = IMSSOFFLIN14_A266DFElemFormMetadata[0] ;
         n266DFElemFormMetadata = IMSSOFFLIN14_n266DFElemFormMetadata[0] ;
         A267DFElemFormShwNbr = IMSSOFFLIN14_A267DFElemFormShwNbr[0] ;
         n267DFElemFormShwNbr = IMSSOFFLIN14_n267DFElemFormShwNbr[0] ;
         A265DFElemFormDateSel = IMSSOFFLIN14_A265DFElemFormDateSel[0] ;
         n265DFElemFormDateSel = IMSSOFFLIN14_n265DFElemFormDateSel[0] ;
         A262DFElemFormHasPmpt = IMSSOFFLIN14_A262DFElemFormHasPmpt[0] ;
         n262DFElemFormHasPmpt = IMSSOFFLIN14_n262DFElemFormHasPmpt[0] ;
         A187DFElemFormIsFlt = IMSSOFFLIN14_A187DFElemFormIsFlt[0] ;
         n187DFElemFormIsFlt = IMSSOFFLIN14_n187DFElemFormIsFlt[0] ;
         A186DFElemFormCmpWth = IMSSOFFLIN14_A186DFElemFormCmpWth[0] ;
         n186DFElemFormCmpWth = IMSSOFFLIN14_n186DFElemFormCmpWth[0] ;
         A185DFElemFormLblWth = IMSSOFFLIN14_A185DFElemFormLblWth[0] ;
         n185DFElemFormLblWth = IMSSOFFLIN14_n185DFElemFormLblWth[0] ;
         A285DFElemFormPrtShwNbr = IMSSOFFLIN14_A285DFElemFormPrtShwNbr[0] ;
         A284DFElemFormPrtNumColSkip = IMSSOFFLIN14_A284DFElemFormPrtNumColSkip[0] ;
         A276DFElemFormPrtNumRowSkip = IMSSOFFLIN14_A276DFElemFormPrtNumRowSkip[0] ;
         A274DFElemFormPrtAddRows = IMSSOFFLIN14_A274DFElemFormPrtAddRows[0] ;
         A273DFElemFormPrtName = IMSSOFFLIN14_A273DFElemFormPrtName[0] ;
         A194DFElemFormIsVisPrt = IMSSOFFLIN14_A194DFElemFormIsVisPrt[0] ;
         A193DFElemFormIsVis = IMSSOFFLIN14_A193DFElemFormIsVis[0] ;
         A192DFElemFormIsColap = IMSSOFFLIN14_A192DFElemFormIsColap[0] ;
         A191DFElemFormAllowIns = IMSSOFFLIN14_A191DFElemFormAllowIns[0] ;
         n191DFElemFormAllowIns = IMSSOFFLIN14_n191DFElemFormAllowIns[0] ;
         A190DFElemFormAllowUpd = IMSSOFFLIN14_A190DFElemFormAllowUpd[0] ;
         n190DFElemFormAllowUpd = IMSSOFFLIN14_n190DFElemFormAllowUpd[0] ;
         A189DFElemFormAllowDlt = IMSSOFFLIN14_A189DFElemFormAllowDlt[0] ;
         n189DFElemFormAllowDlt = IMSSOFFLIN14_n189DFElemFormAllowDlt[0] ;
         A184DFElemFormInhType = IMSSOFFLIN14_A184DFElemFormInhType[0] ;
         A116DFElemFormPos = IMSSOFFLIN14_A116DFElemFormPos[0] ;
         A188DFElemFormName = IMSSOFFLIN14_A188DFElemFormName[0] ;
         A89DFElemVer = IMSSOFFLIN14_A89DFElemVer[0] ;
         A88DFElemId = IMSSOFFLIN14_A88DFElemId[0] ;
         A87DFFormVer = IMSSOFFLIN14_A87DFFormVer[0] ;
         A86DFFormId = IMSSOFFLIN14_A86DFFormId[0] ;
         gxsyncline.add(GXutil.booltostr( A189DFElemFormAllowDlt));
         gxsyncline.add(GXutil.booltostr( A191DFElemFormAllowIns));
         gxsyncline.add(GXutil.booltostr( A190DFElemFormAllowUpd));
         gxsyncline.add(GXutil.rtrim( A186DFElemFormCmpWth));
         gxsyncline.add(GXutil.booltostr( A265DFElemFormDateSel));
         gxsyncline.add(GXutil.booltostr( A262DFElemFormHasPmpt));
         gxsyncline.add(GXutil.rtrim( A184DFElemFormInhType));
         gxsyncline.add(GXutil.booltostr( A192DFElemFormIsColap));
         gxsyncline.add(GXutil.rtrim( A187DFElemFormIsFlt));
         gxsyncline.add(GXutil.booltostr( A193DFElemFormIsVis));
         gxsyncline.add(GXutil.booltostr( A194DFElemFormIsVisPrt));
         gxsyncline.add(GXutil.rtrim( A185DFElemFormLblWth));
         gxsyncline.add(A307DFElemFormLoadRule);
         gxsyncline.add(A266DFElemFormMetadata);
         gxsyncline.add(GXutil.rtrim( A188DFElemFormName));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A116DFElemFormPos, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.booltostr( A274DFElemFormPrtAddRows));
         gxsyncline.add(GXutil.rtrim( A273DFElemFormPrtName));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A284DFElemFormPrtNumColSkip, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A276DFElemFormPrtNumRowSkip, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(A316DFElemFormPrtPic);
         gxsyncline.add(GXutil.booltostr( A285DFElemFormPrtShwNbr));
         gxsyncline.add(GXutil.booltostr( A313DFElemFormReq));
         gxsyncline.add(GXutil.booltostr( A267DFElemFormShwNbr));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A88DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A88DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A89DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A89DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A86DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A86DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A87DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A87DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(12);
      }
      pr_default.close(12);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "DFElemForm" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  DFElemFormInst */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtDFElemFormInst( )
   {
      /* Begin Synchronize  DFElemFormInst */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("DFElemFormInst");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      pr_default.dynParam(13, new Object[]{ new Object[]{
                                           new Long(A90DFFormInstId) ,
                                           AV2ColDFFormInstId },
                                           new int[] {
                                           TypeConstants.LONG, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN15 */
      pr_default.execute(13);
      while ( (pr_default.getStatus(13) != 101) )
      {
         A147DFElemFormInstFileName = IMSSOFFLIN15_A147DFElemFormInstFileName[0] ;
         n147DFElemFormInstFileName = IMSSOFFLIN15_n147DFElemFormInstFileName[0] ;
         A146DFElemFormInstFileType = IMSSOFFLIN15_A146DFElemFormInstFileType[0] ;
         n146DFElemFormInstFileType = IMSSOFFLIN15_n146DFElemFormInstFileType[0] ;
         A145DFElemFormInstBlob = IMSSOFFLIN15_A145DFElemFormInstBlob[0] ;
         n145DFElemFormInstBlob = IMSSOFFLIN15_n145DFElemFormInstBlob[0] ;
         A143DFElemFormInstVal = IMSSOFFLIN15_A143DFElemFormInstVal[0] ;
         n143DFElemFormInstVal = IMSSOFFLIN15_n143DFElemFormInstVal[0] ;
         A89DFElemVer = IMSSOFFLIN15_A89DFElemVer[0] ;
         A88DFElemId = IMSSOFFLIN15_A88DFElemId[0] ;
         A90DFFormInstId = IMSSOFFLIN15_A90DFFormInstId[0] ;
         gxsyncline.add(GXutil.getRelativeBlobFile( A145DFElemFormInstBlob));
         gxsyncline.add(GXutil.rtrim( A147DFElemFormInstFileName));
         gxsyncline.add(GXutil.rtrim( A146DFElemFormInstFileType));
         gxsyncline.add(A143DFElemFormInstVal);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A88DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A88DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A89DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A89DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A90DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A90DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(13);
      }
      pr_default.close(13);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "DFElemFormInst" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  DFElemFormInstSubElem */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtDFElemFormInstSubElem( )
   {
      /* Begin Synchronize  DFElemFormInstSubElem */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("DFElemFormInstSubElem");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      pr_default.dynParam(14, new Object[]{ new Object[]{
                                           new Long(A90DFFormInstId) ,
                                           AV2ColDFFormInstId },
                                           new int[] {
                                           TypeConstants.LONG, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN16 */
      pr_default.execute(14);
      while ( (pr_default.getStatus(14) != 101) )
      {
         A150DFElemFormInstSubElemFileName = IMSSOFFLIN16_A150DFElemFormInstSubElemFileName[0] ;
         n150DFElemFormInstSubElemFileName = IMSSOFFLIN16_n150DFElemFormInstSubElemFileName[0] ;
         A149DFElemFormInstSubElemFileType = IMSSOFFLIN16_A149DFElemFormInstSubElemFileType[0] ;
         n149DFElemFormInstSubElemFileType = IMSSOFFLIN16_n149DFElemFormInstSubElemFileType[0] ;
         A108DFSubElemFormElemId = IMSSOFFLIN16_A108DFSubElemFormElemId[0] ;
         A109DFSubElemFormElemVer = IMSSOFFLIN16_A109DFSubElemFormElemVer[0] ;
         A110DFElemFormInstSubElemRow = IMSSOFFLIN16_A110DFElemFormInstSubElemRow[0] ;
         A144DFElemFormInstSubElemVal = IMSSOFFLIN16_A144DFElemFormInstSubElemVal[0] ;
         n144DFElemFormInstSubElemVal = IMSSOFFLIN16_n144DFElemFormInstSubElemVal[0] ;
         A148DFElemFormInstSubElemBlob = IMSSOFFLIN16_A148DFElemFormInstSubElemBlob[0] ;
         n148DFElemFormInstSubElemBlob = IMSSOFFLIN16_n148DFElemFormInstSubElemBlob[0] ;
         A107DFElemFormInstSubElemId = IMSSOFFLIN16_A107DFElemFormInstSubElemId[0] ;
         A89DFElemVer = IMSSOFFLIN16_A89DFElemVer[0] ;
         A88DFElemId = IMSSOFFLIN16_A88DFElemId[0] ;
         A90DFFormInstId = IMSSOFFLIN16_A90DFFormInstId[0] ;
         gxsyncline.add(GXutil.getRelativeBlobFile( A148DFElemFormInstSubElemBlob));
         gxsyncline.add(GXutil.rtrim( A150DFElemFormInstSubElemFileName));
         gxsyncline.add(GXutil.rtrim( A149DFElemFormInstSubElemFileType));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A107DFElemFormInstSubElemId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A107DFElemFormInstSubElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A110DFElemFormInstSubElemRow, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(A144DFElemFormInstSubElemVal);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A88DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A88DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A89DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A89DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A90DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A90DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A108DFSubElemFormElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A109DFSubElemFormElemVer, (byte)(6), (byte)(0), ".", "")));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(14);
      }
      pr_default.close(14);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "DFElemFormInstSubElem" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  DFTemp */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtDFTemp( )
   {
      /* Begin Synchronize  DFTemp */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("DFTemp");
      gxsyncresponse.add(gxsyncheader);
	  gxsyncresponse_hash = new com.genexus.GxUnknownObjectCollection();
	  gxsyncresponse_hash.add(gxsyncheader);	  
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsyncline_hash = new com.genexus.internet.StringCollection() ;	  
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN17 */
      pr_default.execute(15);
      while ( (pr_default.getStatus(15) != 101) )
      {
         A290DFTempFm = IMSSOFFLIN17_A290DFTempFm[0] ;
         A287DFTempOutFm = IMSSOFFLIN17_A287DFTempOutFm[0] ;
         A281DFTempAddParmPrgName = IMSSOFFLIN17_A281DFTempAddParmPrgName[0] ;
         A280DFTempBlob = IMSSOFFLIN17_A280DFTempBlob[0] ;
         A286DFTempDsc = IMSSOFFLIN17_A286DFTempDsc[0] ;
         A136DFTempName = IMSSOFFLIN17_A136DFTempName[0] ;
         A87DFFormVer = IMSSOFFLIN17_A87DFFormVer[0] ;
         A86DFFormId = IMSSOFFLIN17_A86DFFormId[0] ;
		 
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A86DFFormId, (byte)(6), (byte)(0), ".", "")));
		 gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A86DFFormId, (byte)(6), (byte)(0), ".", "")));		 
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A86DFFormId, (byte)(6), (byte)(0), ".", "")));

         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A87DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A87DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A87DFFormVer, (byte)(6), (byte)(0), ".", "")));
		 
         gxsyncline.add(A281DFTempAddParmPrgName);
		 gxsyncline_hash.add(A281DFTempAddParmPrgName);
		 
		 //gxsyncline_hash path de Blobs no se agregan a la sincronizacion
         gxsyncline.add(GXutil.getRelativeBlobFile( A280DFTempBlob));
		 
         gxsyncline.add(A286DFTempDsc);
		 gxsyncline_hash.add(A286DFTempDsc);
		 
         gxsyncline.add(GXutil.rtrim( A290DFTempFm));
		 gxsyncline_hash.add(GXutil.rtrim( A290DFTempFm));
		 
         gxsyncline.add(GXutil.rtrim( A136DFTempName));
		 gxsyncline_hash.add(GXutil.rtrim( A136DFTempName));
         gxsynchashkey.add(GXutil.rtrim( A136DFTempName));
		 
         gxsyncline.add(GXutil.rtrim( A287DFTempOutFm));
		 gxsyncline_hash.add(GXutil.rtrim( A287DFTempOutFm));
		 
         //gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
		 gxlinehash = GXutil.getMD5Hash( gxsyncline_hash.ToJavascriptSource()) ;
		 
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
		 gxsyncresponse_hash.add(gxsyncline_hash);
         gxsyncline = new com.genexus.internet.StringCollection() ;
		 gxsyncline_hash = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(15);
      }
      pr_default.close(15);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      //gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
	  gxtablecurrenthash = GXutil.getMD5Hash( gxsyncresponse_hash.toJSonString(false)) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "DFTemp" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  DFDomStaVals */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtDFDomStaVals( )
   {
      /* Begin Synchronize  DFDomStaVals */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("DFDomStaVals");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN18 */
      pr_default.execute(16);
      while ( (pr_default.getStatus(16) != 101) )
      {
         A225DFDomStaValOptDsc = IMSSOFFLIN18_A225DFDomStaValOptDsc[0] ;
         A113DFDomStaValOptOrd = IMSSOFFLIN18_A113DFDomStaValOptOrd[0] ;
         A112DFDomStaValOptCod = IMSSOFFLIN18_A112DFDomStaValOptCod[0] ;
         A111DFDomId = IMSSOFFLIN18_A111DFDomId[0] ;
         n111DFDomId = IMSSOFFLIN18_n111DFDomId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A111DFDomId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A111DFDomId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A112DFDomStaValOptCod));
         gxsynchashkey.add(GXutil.rtrim( A112DFDomStaValOptCod));
         gxsyncline.add(GXutil.rtrim( A225DFDomStaValOptDsc));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A113DFDomStaValOptOrd, (byte)(6), (byte)(0), ".", "")));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(16);
      }
      pr_default.close(16);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "DFDomStaVals" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  DFFormInst */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtDFFormInst( )
   {
      /* Begin Synchronize  DFFormInst */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("DFFormInst");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      pr_default.dynParam(17, new Object[]{ new Object[]{
                                           new Long(A90DFFormInstId) ,
                                           AV2ColDFFormInstId },
                                           new int[] {
                                           TypeConstants.LONG, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN19 */
      pr_default.execute(17);
      while ( (pr_default.getStatus(17) != 101) )
      {
         A200DFFormInstSignedPDF = IMSSOFFLIN19_A200DFFormInstSignedPDF[0] ;
         n200DFFormInstSignedPDF = IMSSOFFLIN19_n200DFFormInstSignedPDF[0] ;
         A201DFFormInstSignedBy = IMSSOFFLIN19_A201DFFormInstSignedBy[0] ;
         n201DFFormInstSignedBy = IMSSOFFLIN19_n201DFFormInstSignedBy[0] ;
         A157DFFormInstDT = IMSSOFFLIN19_A157DFFormInstDT[0] ;
         A106DFFormInstFormVer = IMSSOFFLIN19_A106DFFormInstFormVer[0] ;
         A105DFFormInstFormId = IMSSOFFLIN19_A105DFFormInstFormId[0] ;
         A90DFFormInstId = IMSSOFFLIN19_A90DFFormInstId[0] ;
         gxsyncline.add(GXutil.timeToCharREST( A157DFFormInstDT));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A105DFFormInstFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A106DFFormInstFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A90DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A90DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsyncline.add(A201DFFormInstSignedBy);
         gxsyncline.add(GXutil.getRelativeBlobFile( A200DFFormInstSignedPDF));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(17);
      }
      pr_default.close(17);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "DFFormInst" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  DFElem */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtDFElem( )
   {
      /* Begin Synchronize  DFElem */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("DFElem");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN20 */
      pr_default.execute(18);
      while ( (pr_default.getStatus(18) != 101) )
      {
         A314DFElemReq = IMSSOFFLIN20_A314DFElemReq[0] ;
         A315DFElemPrtPic = IMSSOFFLIN20_A315DFElemPrtPic[0] ;
         A308DFElemLoadRule = IMSSOFFLIN20_A308DFElemLoadRule[0] ;
         n308DFElemLoadRule = IMSSOFFLIN20_n308DFElemLoadRule[0] ;
         A268DFElemMetadata = IMSSOFFLIN20_A268DFElemMetadata[0] ;
         n268DFElemMetadata = IMSSOFFLIN20_n268DFElemMetadata[0] ;
         A241DFElemIsColap = IMSSOFFLIN20_A241DFElemIsColap[0] ;
         A283DFElemPrtShwNbr = IMSSOFFLIN20_A283DFElemPrtShwNbr[0] ;
         A282DFElemPrtNumColSkip = IMSSOFFLIN20_A282DFElemPrtNumColSkip[0] ;
         A277DFElemPrtNumRowSkip = IMSSOFFLIN20_A277DFElemPrtNumRowSkip[0] ;
         A275DFElemPrtAddRows = IMSSOFFLIN20_A275DFElemPrtAddRows[0] ;
         A272DFElemPrtName = IMSSOFFLIN20_A272DFElemPrtName[0] ;
         A263DFElemIsVisPrt = IMSSOFFLIN20_A263DFElemIsVisPrt[0] ;
         A240DFElemIsVis = IMSSOFFLIN20_A240DFElemIsVis[0] ;
         A260DFElemLblWth = IMSSOFFLIN20_A260DFElemLblWth[0] ;
         n260DFElemLblWth = IMSSOFFLIN20_n260DFElemLblWth[0] ;
         A246DFElemCmpWth = IMSSOFFLIN20_A246DFElemCmpWth[0] ;
         n246DFElemCmpWth = IMSSOFFLIN20_n246DFElemCmpWth[0] ;
         A245DFElemIsFlt = IMSSOFFLIN20_A245DFElemIsFlt[0] ;
         n245DFElemIsFlt = IMSSOFFLIN20_n245DFElemIsFlt[0] ;
         A259DFElemFileType = IMSSOFFLIN20_A259DFElemFileType[0] ;
         n259DFElemFileType = IMSSOFFLIN20_n259DFElemFileType[0] ;
         A257DFElemRegexVal = IMSSOFFLIN20_A257DFElemRegexVal[0] ;
         n257DFElemRegexVal = IMSSOFFLIN20_n257DFElemRegexVal[0] ;
         A256DFElemAllowDlt = IMSSOFFLIN20_A256DFElemAllowDlt[0] ;
         n256DFElemAllowDlt = IMSSOFFLIN20_n256DFElemAllowDlt[0] ;
         A255DFElemAllowUpd = IMSSOFFLIN20_A255DFElemAllowUpd[0] ;
         n255DFElemAllowUpd = IMSSOFFLIN20_n255DFElemAllowUpd[0] ;
         A254DFElemAllowIns = IMSSOFFLIN20_A254DFElemAllowIns[0] ;
         n254DFElemAllowIns = IMSSOFFLIN20_n254DFElemAllowIns[0] ;
         A253DFElemUseBtns = IMSSOFFLIN20_A253DFElemUseBtns[0] ;
         n253DFElemUseBtns = IMSSOFFLIN20_n253DFElemUseBtns[0] ;
         A252DFElemIsOrd = IMSSOFFLIN20_A252DFElemIsOrd[0] ;
         n252DFElemIsOrd = IMSSOFFLIN20_n252DFElemIsOrd[0] ;
         A251DFElemMaxSuggRes = IMSSOFFLIN20_A251DFElemMaxSuggRes[0] ;
         n251DFElemMaxSuggRes = IMSSOFFLIN20_n251DFElemMaxSuggRes[0] ;
         A250DFElemForceSuggSel = IMSSOFFLIN20_A250DFElemForceSuggSel[0] ;
         n250DFElemForceSuggSel = IMSSOFFLIN20_n250DFElemForceSuggSel[0] ;
         A249DFElemMinCntCharSugg = IMSSOFFLIN20_A249DFElemMinCntCharSugg[0] ;
         n249DFElemMinCntCharSugg = IMSSOFFLIN20_n249DFElemMinCntCharSugg[0] ;
         A261DFElemDscPrgName = IMSSOFFLIN20_A261DFElemDscPrgName[0] ;
         A248DFElemLoadPrgName = IMSSOFFLIN20_A248DFElemLoadPrgName[0] ;
         n248DFElemLoadPrgName = IMSSOFFLIN20_n248DFElemLoadPrgName[0] ;
         A270DFElemBtnPos = IMSSOFFLIN20_A270DFElemBtnPos[0] ;
         n270DFElemBtnPos = IMSSOFFLIN20_n270DFElemBtnPos[0] ;
         A271DFElemShwNbrLbl = IMSSOFFLIN20_A271DFElemShwNbrLbl[0] ;
         n271DFElemShwNbrLbl = IMSSOFFLIN20_n271DFElemShwNbrLbl[0] ;
         A269DFElemShwNbr = IMSSOFFLIN20_A269DFElemShwNbr[0] ;
         n269DFElemShwNbr = IMSSOFFLIN20_n269DFElemShwNbr[0] ;
         A264DFElemDateSel = IMSSOFFLIN20_A264DFElemDateSel[0] ;
         n264DFElemDateSel = IMSSOFFLIN20_n264DFElemDateSel[0] ;
         A247DFElemHasPmpt = IMSSOFFLIN20_A247DFElemHasPmpt[0] ;
         n247DFElemHasPmpt = IMSSOFFLIN20_n247DFElemHasPmpt[0] ;
         A183DFElemDftVal = IMSSOFFLIN20_A183DFElemDftVal[0] ;
         n183DFElemDftVal = IMSSOFFLIN20_n183DFElemDftVal[0] ;
         A244DFElemCntCols = IMSSOFFLIN20_A244DFElemCntCols[0] ;
         n244DFElemCntCols = IMSSOFFLIN20_n244DFElemCntCols[0] ;
         A243DFElemCntRows = IMSSOFFLIN20_A243DFElemCntRows[0] ;
         n243DFElemCntRows = IMSSOFFLIN20_n243DFElemCntRows[0] ;
         A242DFElemCntDec = IMSSOFFLIN20_A242DFElemCntDec[0] ;
         n242DFElemCntDec = IMSSOFFLIN20_n242DFElemCntDec[0] ;
         A258DFElemWth = IMSSOFFLIN20_A258DFElemWth[0] ;
         n258DFElemWth = IMSSOFFLIN20_n258DFElemWth[0] ;
         A239DFElemLen = IMSSOFFLIN20_A239DFElemLen[0] ;
         n239DFElemLen = IMSSOFFLIN20_n239DFElemLen[0] ;
         A199DFElemDsp = IMSSOFFLIN20_A199DFElemDsp[0] ;
         n199DFElemDsp = IMSSOFFLIN20_n199DFElemDsp[0] ;
         A181DFElemType = IMSSOFFLIN20_A181DFElemType[0] ;
         A111DFDomId = IMSSOFFLIN20_A111DFDomId[0] ;
         n111DFDomId = IMSSOFFLIN20_n111DFDomId[0] ;
         A195DFElemClsName = IMSSOFFLIN20_A195DFElemClsName[0] ;
         n195DFElemClsName = IMSSOFFLIN20_n195DFElemClsName[0] ;
         A238DFElemDsc = IMSSOFFLIN20_A238DFElemDsc[0] ;
         n238DFElemDsc = IMSSOFFLIN20_n238DFElemDsc[0] ;
         A151DFElemName = IMSSOFFLIN20_A151DFElemName[0] ;
         A114DFElemGuid = IMSSOFFLIN20_A114DFElemGuid[0] ;
         A89DFElemVer = IMSSOFFLIN20_A89DFElemVer[0] ;
         A88DFElemId = IMSSOFFLIN20_A88DFElemId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A111DFDomId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.booltostr( A256DFElemAllowDlt));
         gxsyncline.add(GXutil.booltostr( A254DFElemAllowIns));
         gxsyncline.add(GXutil.booltostr( A255DFElemAllowUpd));
         gxsyncline.add(GXutil.rtrim( A270DFElemBtnPos));
         gxsyncline.add(GXutil.rtrim( A195DFElemClsName));
         gxsyncline.add(GXutil.rtrim( A246DFElemCmpWth));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A244DFElemCntCols, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A242DFElemCntDec, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A243DFElemCntRows, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.booltostr( A264DFElemDateSel));
         gxsyncline.add(GXutil.rtrim( A183DFElemDftVal));
         gxsyncline.add(A238DFElemDsc);
         gxsyncline.add(A261DFElemDscPrgName);
         gxsyncline.add(GXutil.rtrim( A199DFElemDsp));
         gxsyncline.add(GXutil.rtrim( A259DFElemFileType));
         gxsyncline.add(GXutil.booltostr( A250DFElemForceSuggSel));
         gxsyncline.add(A114DFElemGuid.toString());
         gxsyncline.add(GXutil.booltostr( A247DFElemHasPmpt));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A88DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A88DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.booltostr( A241DFElemIsColap));
         gxsyncline.add(GXutil.rtrim( A245DFElemIsFlt));
         gxsyncline.add(GXutil.booltostr( A252DFElemIsOrd));
         gxsyncline.add(GXutil.booltostr( A240DFElemIsVis));
         gxsyncline.add(GXutil.booltostr( A263DFElemIsVisPrt));
         gxsyncline.add(GXutil.rtrim( A260DFElemLblWth));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A239DFElemLen, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(A248DFElemLoadPrgName);
         gxsyncline.add(A308DFElemLoadRule);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A251DFElemMaxSuggRes, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(A268DFElemMetadata);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A249DFElemMinCntCharSugg, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A151DFElemName));
         gxsyncline.add(GXutil.booltostr( A275DFElemPrtAddRows));
         gxsyncline.add(GXutil.rtrim( A272DFElemPrtName));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A282DFElemPrtNumColSkip, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A277DFElemPrtNumRowSkip, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(A315DFElemPrtPic);
         gxsyncline.add(GXutil.booltostr( A283DFElemPrtShwNbr));
         gxsyncline.add(GXutil.rtrim( A257DFElemRegexVal));
         gxsyncline.add(GXutil.booltostr( A314DFElemReq));
         gxsyncline.add(GXutil.booltostr( A269DFElemShwNbr));
         gxsyncline.add(GXutil.rtrim( A271DFElemShwNbrLbl));
         gxsyncline.add(GXutil.rtrim( A181DFElemType));
         gxsyncline.add(GXutil.booltostr( A253DFElemUseBtns));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A89DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A89DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A258DFElemWth, (byte)(6), (byte)(0), ".", "")));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(18);
      }
      pr_default.close(18);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "DFElem" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  DFFormRst */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtDFFormRst( )
   {
      /* Begin Synchronize  DFFormRst */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("DFFormRst");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN21 */
      pr_default.execute(19);
      while ( (pr_default.getStatus(19) != 101) )
      {
         A93DFFormRstVal = IMSSOFFLIN21_A93DFFormRstVal[0] ;
         A92DFFormRstId = IMSSOFFLIN21_A92DFFormRstId[0] ;
         A87DFFormVer = IMSSOFFLIN21_A87DFFormVer[0] ;
         A86DFFormId = IMSSOFFLIN21_A86DFFormId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A86DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A86DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A92DFFormRstId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A92DFFormRstId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A93DFFormRstVal));
         gxsynchashkey.add(GXutil.rtrim( A93DFFormRstVal));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A87DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A87DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(19);
      }
      pr_default.close(19);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "DFFormRst" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  DFUserRst */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtDFUserRst( )
   {
      /* Begin Synchronize  DFUserRst */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("DFUserRst");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN22 */
      pr_default.execute(20);
      while ( (pr_default.getStatus(20) != 101) )
      {
         A166DFUserRstPwdIni = IMSSOFFLIN22_A166DFUserRstPwdIni[0] ;
         A101DFUserRstVal = IMSSOFFLIN22_A101DFUserRstVal[0] ;
         A100DFUserRstId = IMSSOFFLIN22_A100DFUserRstId[0] ;
         A99DFUserExtId = IMSSOFFLIN22_A99DFUserExtId[0] ;
         gxsyncline.add(A99DFUserExtId);
         gxsynchashkey.add(A99DFUserExtId);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A100DFUserRstId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A100DFUserRstId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.booltostr( A166DFUserRstPwdIni));
         gxsyncline.add(GXutil.rtrim( A101DFUserRstVal));
         gxsynchashkey.add(GXutil.rtrim( A101DFUserRstVal));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(20);
      }
      pr_default.close(20);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "DFUserRst" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  DFDom */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtDFDom( )
   {
      /* Begin Synchronize  DFDom */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("DFDom");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN23 */
      pr_default.execute(21);
      while ( (pr_default.getStatus(21) != 101) )
      {
         A319DFDomPrtDsc = IMSSOFFLIN23_A319DFDomPrtDsc[0] ;
         n319DFDomPrtDsc = IMSSOFFLIN23_n319DFDomPrtDsc[0] ;
         A226DFDomLblWth = IMSSOFFLIN23_A226DFDomLblWth[0] ;
         n226DFDomLblWth = IMSSOFFLIN23_n226DFDomLblWth[0] ;
         A222DFDomCmpWth = IMSSOFFLIN23_A222DFDomCmpWth[0] ;
         n222DFDomCmpWth = IMSSOFFLIN23_n222DFDomCmpWth[0] ;
         A221DFDomIsFlt = IMSSOFFLIN23_A221DFDomIsFlt[0] ;
         n221DFDomIsFlt = IMSSOFFLIN23_n221DFDomIsFlt[0] ;
         A224DFDomFileType = IMSSOFFLIN23_A224DFDomFileType[0] ;
         n224DFDomFileType = IMSSOFFLIN23_n224DFDomFileType[0] ;
         A220DFDomRegexVal = IMSSOFFLIN23_A220DFDomRegexVal[0] ;
         A216DFDomAllowDlt = IMSSOFFLIN23_A216DFDomAllowDlt[0] ;
         n216DFDomAllowDlt = IMSSOFFLIN23_n216DFDomAllowDlt[0] ;
         A215DFDomAllowUpd = IMSSOFFLIN23_A215DFDomAllowUpd[0] ;
         n215DFDomAllowUpd = IMSSOFFLIN23_n215DFDomAllowUpd[0] ;
         A214DFDomAllowIns = IMSSOFFLIN23_A214DFDomAllowIns[0] ;
         n214DFDomAllowIns = IMSSOFFLIN23_n214DFDomAllowIns[0] ;
         A213DFDomUseBtns = IMSSOFFLIN23_A213DFDomUseBtns[0] ;
         n213DFDomUseBtns = IMSSOFFLIN23_n213DFDomUseBtns[0] ;
         A212DFDomIsOrd = IMSSOFFLIN23_A212DFDomIsOrd[0] ;
         n212DFDomIsOrd = IMSSOFFLIN23_n212DFDomIsOrd[0] ;
         A210DFDomMaxSuggRes = IMSSOFFLIN23_A210DFDomMaxSuggRes[0] ;
         n210DFDomMaxSuggRes = IMSSOFFLIN23_n210DFDomMaxSuggRes[0] ;
         A209DFDomForceSuggSel = IMSSOFFLIN23_A209DFDomForceSuggSel[0] ;
         n209DFDomForceSuggSel = IMSSOFFLIN23_n209DFDomForceSuggSel[0] ;
         A208DFDomMinCntCharSugg = IMSSOFFLIN23_A208DFDomMinCntCharSugg[0] ;
         n208DFDomMinCntCharSugg = IMSSOFFLIN23_n208DFDomMinCntCharSugg[0] ;
         A211DFDomDftVal = IMSSOFFLIN23_A211DFDomDftVal[0] ;
         n211DFDomDftVal = IMSSOFFLIN23_n211DFDomDftVal[0] ;
         A219DFDomCntCols = IMSSOFFLIN23_A219DFDomCntCols[0] ;
         A218DFDomCntRows = IMSSOFFLIN23_A218DFDomCntRows[0] ;
         A217DFDomCntDec = IMSSOFFLIN23_A217DFDomCntDec[0] ;
         A223DFDomWth = IMSSOFFLIN23_A223DFDomWth[0] ;
         A207DFDomLen = IMSSOFFLIN23_A207DFDomLen[0] ;
         A198DFDomDsp = IMSSOFFLIN23_A198DFDomDsp[0] ;
         n198DFDomDsp = IMSSOFFLIN23_n198DFDomDsp[0] ;
         A197DFDomType = IMSSOFFLIN23_A197DFDomType[0] ;
         A227DFDomGUID = IMSSOFFLIN23_A227DFDomGUID[0] ;
         A206DFDomDsc = IMSSOFFLIN23_A206DFDomDsc[0] ;
         A111DFDomId = IMSSOFFLIN23_A111DFDomId[0] ;
         n111DFDomId = IMSSOFFLIN23_n111DFDomId[0] ;
         gxsyncline.add(GXutil.booltostr( A216DFDomAllowDlt));
         gxsyncline.add(GXutil.booltostr( A214DFDomAllowIns));
         gxsyncline.add(GXutil.booltostr( A215DFDomAllowUpd));
         gxsyncline.add(GXutil.rtrim( A222DFDomCmpWth));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A219DFDomCntCols, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A217DFDomCntDec, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A218DFDomCntRows, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A211DFDomDftVal));
         gxsyncline.add(GXutil.rtrim( A206DFDomDsc));
         gxsyncline.add(GXutil.rtrim( A198DFDomDsp));
         gxsyncline.add(GXutil.rtrim( A224DFDomFileType));
         gxsyncline.add(GXutil.booltostr( A209DFDomForceSuggSel));
         gxsyncline.add(A227DFDomGUID.toString());
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A111DFDomId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A111DFDomId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A221DFDomIsFlt));
         gxsyncline.add(GXutil.booltostr( A212DFDomIsOrd));
         gxsyncline.add(GXutil.rtrim( A226DFDomLblWth));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A207DFDomLen, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A210DFDomMaxSuggRes, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A208DFDomMinCntCharSugg, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.booltostr( A319DFDomPrtDsc));
         gxsyncline.add(GXutil.rtrim( A220DFDomRegexVal));
         gxsyncline.add(GXutil.rtrim( A197DFDomType));
         gxsyncline.add(GXutil.booltostr( A213DFDomUseBtns));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A223DFDomWth, (byte)(6), (byte)(0), ".", "")));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(21);
      }
      pr_default.close(21);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "DFDom" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  DFSubElemForm */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtDFSubElemForm( )
   {
      /* Begin Synchronize  DFSubElemForm */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("DFSubElemForm");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN24 */
      pr_default.execute(22);
      while ( (pr_default.getStatus(22) != 101) )
      {
         A117DFSubElemFormPos = IMSSOFFLIN24_A117DFSubElemFormPos[0] ;
         n117DFSubElemFormPos = IMSSOFFLIN24_n117DFSubElemFormPos[0] ;
         A109DFSubElemFormElemVer = IMSSOFFLIN24_A109DFSubElemFormElemVer[0] ;
         A108DFSubElemFormElemId = IMSSOFFLIN24_A108DFSubElemFormElemId[0] ;
         A89DFElemVer = IMSSOFFLIN24_A89DFElemVer[0] ;
         A88DFElemId = IMSSOFFLIN24_A88DFElemId[0] ;
         A87DFFormVer = IMSSOFFLIN24_A87DFFormVer[0] ;
         A86DFFormId = IMSSOFFLIN24_A86DFFormId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A88DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A88DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A89DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A89DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A86DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A86DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A87DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A87DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A108DFSubElemFormElemId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A108DFSubElemFormElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A109DFSubElemFormElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A109DFSubElemFormElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A117DFSubElemFormPos, (byte)(6), (byte)(0), ".", "")));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(22);
      }
      pr_default.close(22);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "DFSubElemForm" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  DFFilElemForm */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtDFFilElemForm( )
   {
      /* Begin Synchronize  DFFilElemForm */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("DFFilElemForm");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN25 */
      pr_default.execute(23);
      while ( (pr_default.getStatus(23) != 101) )
      {
         A120DFFilElemFormElemVer = IMSSOFFLIN25_A120DFFilElemFormElemVer[0] ;
         A119DFFilElemFormElemId = IMSSOFFLIN25_A119DFFilElemFormElemId[0] ;
         A121DFFilElemFormPos = IMSSOFFLIN25_A121DFFilElemFormPos[0] ;
         A118DFFilElemFormId = IMSSOFFLIN25_A118DFFilElemFormId[0] ;
         A89DFElemVer = IMSSOFFLIN25_A89DFElemVer[0] ;
         A88DFElemId = IMSSOFFLIN25_A88DFElemId[0] ;
         A87DFFormVer = IMSSOFFLIN25_A87DFFormVer[0] ;
         A86DFFormId = IMSSOFFLIN25_A86DFFormId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A88DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A88DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A89DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A89DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A119DFFilElemFormElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A120DFFilElemFormElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A118DFFilElemFormId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A118DFFilElemFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A121DFFilElemFormPos, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A86DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A86DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A87DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A87DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(23);
      }
      pr_default.close(23);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "DFFilElemForm" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Full)  Servicio */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtServicio( )
   {
      /* Begin Synchronize  Servicio */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("Servicio");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN26 */
      pr_default.execute(24);
      while ( (pr_default.getStatus(24) != 101) )
      {
         A288HospitalId = IMSSOFFLIN26_A288HospitalId[0] ;
         n288HospitalId = IMSSOFFLIN26_n288HospitalId[0] ;
         A36ServicioDescripcion = IMSSOFFLIN26_A36ServicioDescripcion[0] ;
         A6ServicioId = IMSSOFFLIN26_A6ServicioId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A288HospitalId, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A36ServicioDescripcion));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A6ServicioId, (byte)(4), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A6ServicioId, (byte)(4), (byte)(0), ".", "")));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(24);
      }
      pr_default.close(24);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "Servicio" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   /*  Synchronize for table (Partial)  DFUpl */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtDFUpl( )
   {
      /* Begin Synchronize  DFUpl */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("DFUpl");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      pr_default.dynParam(25, new Object[]{ new Object[]{
                                           new Long(A90DFFormInstId) ,
                                           AV2ColDFFormInstId },
                                           new int[] {
                                           TypeConstants.LONG, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN27 */
      pr_default.execute(25);
      while ( (pr_default.getStatus(25) != 101) )
      {
         A105DFFormInstFormId = IMSSOFFLIN27_A105DFFormInstFormId[0] ;
         A141DFUplFileExt = IMSSOFFLIN27_A141DFUplFileExt[0] ;
         A142DFUplFileName = IMSSOFFLIN27_A142DFUplFileName[0] ;
         A140DFUplFile = IMSSOFFLIN27_A140DFUplFile[0] ;
         A91DFUplKey = IMSSOFFLIN27_A91DFUplKey[0] ;
         A90DFFormInstId = IMSSOFFLIN27_A90DFFormInstId[0] ;
         A105DFFormInstFormId = IMSSOFFLIN27_A105DFFormInstFormId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A90DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A90DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.getRelativeBlobFile( A140DFUplFile));
         gxsyncline.add(GXutil.rtrim( A141DFUplFileExt));
         gxsyncline.add(GXutil.rtrim( A142DFUplFileName));
         gxsyncline.add(GXutil.rtrim( A91DFUplKey));
         gxsynchashkey.add(GXutil.rtrim( A91DFUplKey));
         gxlinehash = GXutil.getMD5Hash( gxsyncline.ToJavascriptSource()) ;
         gxsetline.add(gxsynchashkey.ToJavascriptSource());
         gxsetline.add(gxlinehash);
         gxsetvalueline.add(gxsynchashkey.ToJavascriptSource());
         gxsetvalueline.add(gxsyncline);
         gxsynchashset.add(gxsetline);
         gxsyncvalueset.add(gxsetvalueline);
         gxsynchashkey = new com.genexus.internet.StringCollection() ;
         gxsetline = new com.genexus.internet.StringCollection() ;
         gxsetvalueline = new com.genexus.GxUnknownObjectCollection() ;
         /*  */
         gxsyncresponse.add(gxsyncline);
         gxsyncline = new com.genexus.internet.StringCollection() ;
         pr_default.readNext(25);
      }
      pr_default.close(25);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
      gxtablecurrenthash = GXutil.getMD5Hash( gxtabledata) ;
      gxtablestoredhash = gxtablemdata.item(2) ;
      if ( GXutil.strcmp(gxtablecurrenthash, gxtablestoredhash) == 0 )
      {
         gxsyncresponse.clear();
         gxfinalsync.clear();
         gxsyncstatus = (short)(0) ;
      }
      else
      {
         if ( gxischeck == 1 )
         {
            gxsyncstatus = (short)(1) ;
         }
         gxsyncheader.add(gxtablecurrenthash);
         if ( gxischeck == 0 )
         {
            /* Store hashed rows */
            gxdeviceidentifier = context.getWorkstationId( remoteHandle) ;
            GXv_objcol_gxjsonable7[0] = gxsyncinsert ;
            GXv_objcol_gxjsonable6[0] = gxsyncupdate ;
            GXv_objcol_gxjsonable5[0] = gxsyncdelete ;
            GXv_int8[0] = gxstatus ;
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "DFUpl" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
            imssofflinedatabase.this.gxsyncinsert = GXv_objcol_gxjsonable7[0] ;
            imssofflinedatabase.this.gxsyncupdate = GXv_objcol_gxjsonable6[0] ;
            imssofflinedatabase.this.gxsyncdelete = GXv_objcol_gxjsonable5[0] ;
            imssofflinedatabase.this.gxstatus = GXv_int8[0] ;
            if ( gxerrorstatus == 0 )
            {
               gxerrorstatus = gxstatus ;
            }
            if ( gxstatus == 0 )
            {
               gxfinalsync.add(gxsyncheader);
               gxfinalsync.add(gxsyncinsert);
               gxfinalsync.add(gxsyncupdate);
               gxfinalsync.add(gxsyncdelete);
            }
         }
      }
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncheader = new com.genexus.internet.StringCollection() ;
      gxsyncresponse = gxfinalsync ;
      gxsyncheaderpre = new com.genexus.internet.StringCollection() ;
      return gxsyncresponse ;
   }

   public com.genexus.GxUnknownObjectCollection gxCheckSync( com.genexus.GxUnknownObjectCollection gxtablehashlist )
   {
      initialize();
      GXStart( ) ;
      gxischeck = (short)(1) ;
      gxsyncstatus = (short)(0) ;
      gxMainSync( gxtablehashlist) ;
      return gxallsyncresponse ;
      /* End function gxCheckSync */
   }

   public com.genexus.GxUnknownObjectCollection gxAllSync( com.genexus.GxUnknownObjectCollection gxtablehashlist )
   {
      initialize();
      GXStart( ) ;
      gxischeck = (short)(0) ;
      gxsyncstatus = (short)(0) ;
      gxMainSync( gxtablehashlist) ;
      return gxallsyncresponse ;
      /* End function gxMainSync */
   }

   public com.genexus.GxUnknownObjectCollection gxMainSync( com.genexus.GxUnknownObjectCollection gxtablehashlist )
   {
      /* Message Metadata */
      gxerrorstatus = (short)(0) ;
      gxsyncheaderline = new com.genexus.internet.StringCollection() ;
      gxsyncheaderline.add("GXMetada");
      gxsyncheaderline.add("0.9");
      gxsyncheaderline.add("gapIsTKixqezqirArD/QzQ==");
      gxallsyncresponse.add(gxsyncheaderline);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
      gxsourcever = gxhttpr.getHeader("GXSynchronizerVersion") ;
      if ( GXutil.strcmp(gxsourcever, "gapIsTKixqezqirArD/QzQ==") != 0 )
      {
         gxerrorstatus = (short)(3) ;
      }
      if ( gxerrorstatus == 0 )
      {
         if ( gxtablehashlist.size() < 26 )
         {
            gxtablehashlist = new com.genexus.GxUnknownObjectCollection() ;
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("Medico");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("PacienteMedicoOffline");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("CIE10");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("ExpedienteDiagnostico");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("Texto");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DFParm");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DXAuxImagen");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DXAuxDocto");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("Paciente");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DFForm");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("FormatoPaciente");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("Extension");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DFElemForm");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DFElemFormInst");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DFElemFormInstSubElem");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DFTemp");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DFDomStaVals");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DFFormInst");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DFElem");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DFFormRst");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DFUserRst");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DFDom");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DFSubElemForm");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DFFilElemForm");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("Servicio");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DFUpl");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
         }
         GXV1 = 1 ;
         while ( ( GXV1 <= gxtablehashlist.size() ) && ( gxsyncstatus == 0 ) )
         {
            gxtablemdata = (com.genexus.internet.StringCollection)gxtablehashlist.elementAt(-1+(int)(GXV1)) ;
            if ( GXutil.strcmp("Medico", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtMedico( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("PacienteMedicoOffline", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtPacienteMedicoOffline( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("CIE10", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtCIE10( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("ExpedienteDiagnostico", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtExpedienteDiagnostico( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("Texto", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtTexto( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("DFParm", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDFParm( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("DXAuxImagen", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDXAuxImagen( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("DXAuxDocto", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDXAuxDocto( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("Paciente", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtPaciente( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("DFForm", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDFForm( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("FormatoPaciente", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtFormatoPaciente( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("Extension", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtExtension( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("DFElemForm", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDFElemForm( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("DFElemFormInst", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDFElemFormInst( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("DFElemFormInstSubElem", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDFElemFormInstSubElem( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("DFTemp", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDFTemp( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("DFDomStaVals", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDFDomStaVals( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("DFFormInst", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDFFormInst( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("DFElem", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDFElem( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("DFFormRst", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDFFormRst( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("DFUserRst", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDFUserRst( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("DFDom", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDFDom( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("DFSubElemForm", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDFSubElemForm( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("DFFilElemForm", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDFFilElemForm( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("Servicio", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtServicio( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("DFUpl", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDFUpl( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            GXV1 = (long)(GXV1+1) ;
         }
      }
      gxsyncheaderline.add(GXutil.ltrim( GXutil.str( gxerrorstatus, 4, 0)));
      if ( gxischeck == 1 )
      {
         gxsyncheaderline.add(GXutil.ltrim( GXutil.str( gxsyncstatus, 4, 0)));
      }
      return gxallsyncresponse ;
      /* End function gxMainSync */
   }

   public void gxconfirmsync( com.genexus.GxUnknownObjectCollection gxtableheadlist )
   {
      initialize();
      GXStart( ) ;
      DEVICEID = context.getWorkstationId( remoteHandle) ;
      GXV1 = 1 ;
      while ( GXV1 <= gxtableheadlist.size() )
      {
         gxtablemdata = (com.genexus.internet.StringCollection)gxtableheadlist.elementAt(-1+(int)(GXV1)) ;
         QUERYID = gxtablemdata.item(1) ;
         RESULTSET = gxtablemdata.item(2) ;
         GXV1 = (long)(GXV1+1) ;
      }
   }

   protected void cleanup( )
   {
      CloseOpenCursors();
   }

   protected void CloseOpenCursors( )
   {
   }

   /* Aggregate/select formulas */
   public void initialize( )
   {
      AV4Matricula = "" ;
      AV5UserMedico = "" ;
      GXt_char1 = "" ;
      GXv_char2 = new String [1] ;
      AV2ColDFFormInstId = new GxObjectCollection(Long.class, "internal", "");
      AV3ColPacienteNSSAgregado = new GxObjectCollection(String.class, "internal", "");
      GXt_objcol_int3 = new GxObjectCollection(Long.class, "internal", "");
      GXv_objcol_int4 = new GxObjectCollection [1] ;
      gxsyncheader = new com.genexus.internet.StringCollection();
      gxsyncline = new com.genexus.internet.StringCollection();
      gxtablemdata = new com.genexus.internet.StringCollection();
      gxsyncresponse = new com.genexus.GxUnknownObjectCollection();
      gxsynchashkey = new com.genexus.internet.StringCollection();
      gxfinalsync = new com.genexus.GxUnknownObjectCollection();
      gxsynchashset = new com.genexus.GxUnknownObjectCollection();
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection();
      scmdbuf = "" ;
      IMSSOFFLIN2_A312MedicoDebeMostarTerm = new boolean[] {false} ;
      IMSSOFFLIN2_A302MedicoDebeValidarDatos = new boolean[] {false} ;
      IMSSOFFLIN2_A300MedicoUltimaActualizacion = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN2_A297MedicoMatricula = new long[1] ;
      IMSSOFFLIN2_n297MedicoMatricula = new boolean[] {false} ;
      IMSSOFFLIN2_A296MedicoApellidoMaterno = new String[] {""} ;
      IMSSOFFLIN2_A295MedicoApellidoPaterno = new String[] {""} ;
      IMSSOFFLIN2_A294MedicoSegundoNombre = new String[] {""} ;
      IMSSOFFLIN2_A293MedicoPrimerNombre = new String[] {""} ;
      IMSSOFFLIN2_A292UserMedico = new String[] {""} ;
      A300MedicoUltimaActualizacion = GXutil.resetTime( GXutil.nullDate() );
      A296MedicoApellidoMaterno = "" ;
      A295MedicoApellidoPaterno = "" ;
      A294MedicoSegundoNombre = "" ;
      A293MedicoPrimerNombre = "" ;
      A292UserMedico = "" ;
      gxlinehash = "" ;
      gxsetline = new com.genexus.internet.StringCollection();
      gxsetvalueline = new com.genexus.GxUnknownObjectCollection();
      gxtabledata = "" ;
      gxtablecurrenthash = "" ;
      gxtablestoredhash = "" ;
      gxdeviceidentifier = "" ;
      gxsyncinsert = new com.genexus.GxUnknownObjectCollection();
      gxsyncupdate = new com.genexus.GxUnknownObjectCollection();
      gxsyncdelete = new com.genexus.GxUnknownObjectCollection();
      gxtablehashlist = new com.genexus.GxUnknownObjectCollection();
      gxsyncheaderpre = new com.genexus.internet.StringCollection();
      A75PacienteNSSAgregado = "" ;
      A81Matricula = "" ;
      IMSSOFFLIN3_A75PacienteNSSAgregado = new String[] {""} ;
      IMSSOFFLIN3_A81Matricula = new String[] {""} ;
      IMSSOFFLIN3_A3PacienteAgregado = new String[] {""} ;
      IMSSOFFLIN3_A2PacienteNSS = new String[] {""} ;
      A3PacienteAgregado = "" ;
      A2PacienteNSS = "" ;
      IMSSOFFLIN4_A69CIECodigo = new String[] {""} ;
      IMSSOFFLIN4_A10CIE10Descripcion = new String[] {""} ;
      IMSSOFFLIN4_A1CIE10Id = new int[1] ;
      A69CIECodigo = "" ;
      A10CIE10Descripcion = "" ;
      IMSSOFFLIN5_A75PacienteNSSAgregado = new String[] {""} ;
      IMSSOFFLIN5_A34MMatricula = new long[1] ;
      IMSSOFFLIN5_n34MMatricula = new boolean[] {false} ;
      IMSSOFFLIN5_A33MApMat = new String[] {""} ;
      IMSSOFFLIN5_n33MApMat = new boolean[] {false} ;
      IMSSOFFLIN5_A32MApPat = new String[] {""} ;
      IMSSOFFLIN5_n32MApPat = new boolean[] {false} ;
      IMSSOFFLIN5_A31MNombre = new String[] {""} ;
      IMSSOFFLIN5_n31MNombre = new boolean[] {false} ;
      IMSSOFFLIN5_A30MBMatricula = new long[1] ;
      IMSSOFFLIN5_n30MBMatricula = new boolean[] {false} ;
      IMSSOFFLIN5_A29MBApMat = new String[] {""} ;
      IMSSOFFLIN5_n29MBApMat = new boolean[] {false} ;
      IMSSOFFLIN5_A28MBApPat = new String[] {""} ;
      IMSSOFFLIN5_n28MBApPat = new boolean[] {false} ;
      IMSSOFFLIN5_A27MBNombre = new String[] {""} ;
      IMSSOFFLIN5_n27MBNombre = new boolean[] {false} ;
      IMSSOFFLIN5_A26JSMatricula = new long[1] ;
      IMSSOFFLIN5_n26JSMatricula = new boolean[] {false} ;
      IMSSOFFLIN5_A25JSApMat = new String[] {""} ;
      IMSSOFFLIN5_n25JSApMat = new boolean[] {false} ;
      IMSSOFFLIN5_A24JSApPat = new String[] {""} ;
      IMSSOFFLIN5_n24JSApPat = new boolean[] {false} ;
      IMSSOFFLIN5_A23JSNombre = new String[] {""} ;
      IMSSOFFLIN5_n23JSNombre = new boolean[] {false} ;
      IMSSOFFLIN5_A22DiagnosticoCirugiaFecha = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN5_n22DiagnosticoCirugiaFecha = new boolean[] {false} ;
      IMSSOFFLIN5_A21DiagnosticoCirugia = new String[] {""} ;
      IMSSOFFLIN5_n21DiagnosticoCirugia = new boolean[] {false} ;
      IMSSOFFLIN5_A20Cama = new String[] {""} ;
      IMSSOFFLIN5_n20Cama = new boolean[] {false} ;
      IMSSOFFLIN5_A6ServicioId = new short[1] ;
      IMSSOFFLIN5_A19DiagnosticoResumen = new String[] {""} ;
      IMSSOFFLIN5_n19DiagnosticoResumen = new boolean[] {false} ;
      IMSSOFFLIN5_A18DiagnosticoComplemento = new String[] {""} ;
      IMSSOFFLIN5_n18DiagnosticoComplemento = new boolean[] {false} ;
      IMSSOFFLIN5_A35DiagnosticoFechaAlta = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN5_n35DiagnosticoFechaAlta = new boolean[] {false} ;
      IMSSOFFLIN5_A17DiagnosticoFechaIngreso = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN5_n17DiagnosticoFechaIngreso = new boolean[] {false} ;
      IMSSOFFLIN5_A1CIE10Id = new int[1] ;
      IMSSOFFLIN5_A3PacienteAgregado = new String[] {""} ;
      IMSSOFFLIN5_A2PacienteNSS = new String[] {""} ;
      A33MApMat = "" ;
      A32MApPat = "" ;
      A31MNombre = "" ;
      A29MBApMat = "" ;
      A28MBApPat = "" ;
      A27MBNombre = "" ;
      A25JSApMat = "" ;
      A24JSApPat = "" ;
      A23JSNombre = "" ;
      A22DiagnosticoCirugiaFecha = GXutil.resetTime( GXutil.nullDate() );
      A21DiagnosticoCirugia = "" ;
      A20Cama = "" ;
      A19DiagnosticoResumen = "" ;
      A18DiagnosticoComplemento = "" ;
      A35DiagnosticoFechaAlta = GXutil.resetTime( GXutil.nullDate() );
      A17DiagnosticoFechaIngreso = GXutil.nullDate() ;
      IMSSOFFLIN6_A323nada = new short[1] ;
      IMSSOFFLIN6_A311TextoDescripcion = new String[] {""} ;
      IMSSOFFLIN6_A310TextoTitulo = new String[] {""} ;
      IMSSOFFLIN6_A309TextoId = new short[1] ;
      A311TextoDescripcion = "" ;
      A310TextoTitulo = "" ;
      IMSSOFFLIN7_A169DFParmIsMetaData = new boolean[] {false} ;
      IMSSOFFLIN7_A168DFParmVal = new String[] {""} ;
      IMSSOFFLIN7_A167DFParmName = new String[] {""} ;
      IMSSOFFLIN7_A102DFParmId = new int[1] ;
      A168DFParmVal = "" ;
      A167DFParmName = "" ;
      IMSSOFFLIN8_A75PacienteNSSAgregado = new String[] {""} ;
      IMSSOFFLIN8_A40000DXAuxImagenImg_GXI = new String[] {""} ;
      IMSSOFFLIN8_A322DXAuxImagenExtension = new String[] {""} ;
      IMSSOFFLIN8_A73DXAuxImagenNombre = new String[] {""} ;
      IMSSOFFLIN8_A16DXAuxImagenUserAlta = new String[] {""} ;
      IMSSOFFLIN8_A15DXAuxImagenFechaAlta = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN8_A14DXAuxImagenImg = new String[] {""} ;
      IMSSOFFLIN8_A5DXAuxImagenId = new short[1] ;
      IMSSOFFLIN8_A1CIE10Id = new int[1] ;
      IMSSOFFLIN8_A3PacienteAgregado = new String[] {""} ;
      IMSSOFFLIN8_A2PacienteNSS = new String[] {""} ;
      A40000DXAuxImagenImg_GXI = "" ;
      A322DXAuxImagenExtension = "" ;
      A73DXAuxImagenNombre = "" ;
      A16DXAuxImagenUserAlta = "" ;
      A15DXAuxImagenFechaAlta = GXutil.resetTime( GXutil.nullDate() );
      A14DXAuxImagenImg = "" ;
      IMSSOFFLIN9_A75PacienteNSSAgregado = new String[] {""} ;
      IMSSOFFLIN9_A74DXAuxDoctoNombre = new String[] {""} ;
      IMSSOFFLIN9_A82DXAuxDoctoExtension = new String[] {""} ;
      IMSSOFFLIN9_A13DXAuxDoctoUserAlta = new String[] {""} ;
      IMSSOFFLIN9_A12DXAuxDoctoFechaAlta = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN9_A11DXAuxDoctoDocumento = new String[] {""} ;
      IMSSOFFLIN9_A4DXAuxDoctoId = new short[1] ;
      IMSSOFFLIN9_A1CIE10Id = new int[1] ;
      IMSSOFFLIN9_A3PacienteAgregado = new String[] {""} ;
      IMSSOFFLIN9_A2PacienteNSS = new String[] {""} ;
      A74DXAuxDoctoNombre = "" ;
      A82DXAuxDoctoExtension = "" ;
      A13DXAuxDoctoUserAlta = "" ;
      A12DXAuxDoctoFechaAlta = GXutil.resetTime( GXutil.nullDate() );
      A11DXAuxDoctoDocumento = "" ;
      IMSSOFFLIN10_A321PacienteServicioId = new short[1] ;
      IMSSOFFLIN10_A298PacienteDiagnosticoPhone = new String[] {""} ;
      IMSSOFFLIN10_A291PacienteCie10Id = new int[1] ;
      IMSSOFFLIN10_A76PAcienteFechaIngreso = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN10_A75PacienteNSSAgregado = new String[] {""} ;
      IMSSOFFLIN10_A72PacienteCama = new String[] {""} ;
      IMSSOFFLIN10_A71PacienteDiagnosticoResumido = new String[] {""} ;
      IMSSOFFLIN10_A70PacienteDiagnostico = new String[] {""} ;
      IMSSOFFLIN10_A68PacienteFechaNacimiento = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN10_A55PacienteNombreCompleto = new String[] {""} ;
      IMSSOFFLIN10_A54PacienteReferencia = new String[] {""} ;
      IMSSOFFLIN10_n54PacienteReferencia = new boolean[] {false} ;
      IMSSOFFLIN10_A53PacienteFamiliar = new String[] {""} ;
      IMSSOFFLIN10_n53PacienteFamiliar = new boolean[] {false} ;
      IMSSOFFLIN10_A52PacienteTelefono = new String[] {""} ;
      IMSSOFFLIN10_n52PacienteTelefono = new boolean[] {false} ;
      IMSSOFFLIN10_A51PacienteGenero = new String[] {""} ;
      IMSSOFFLIN10_n51PacienteGenero = new boolean[] {false} ;
      IMSSOFFLIN10_A50PacienteEdad = new short[1] ;
      IMSSOFFLIN10_A46PacienteApMat = new String[] {""} ;
      IMSSOFFLIN10_n46PacienteApMat = new boolean[] {false} ;
      IMSSOFFLIN10_A45PacienteApPat = new String[] {""} ;
      IMSSOFFLIN10_A44PacienteNombre = new String[] {""} ;
      IMSSOFFLIN10_A3PacienteAgregado = new String[] {""} ;
      IMSSOFFLIN10_A2PacienteNSS = new String[] {""} ;
      A298PacienteDiagnosticoPhone = "" ;
      A76PAcienteFechaIngreso = GXutil.nullDate() ;
      A72PacienteCama = "" ;
      A71PacienteDiagnosticoResumido = "" ;
      A70PacienteDiagnostico = "" ;
      A68PacienteFechaNacimiento = GXutil.nullDate() ;
      A55PacienteNombreCompleto = "" ;
      A54PacienteReferencia = "" ;
      A53PacienteFamiliar = "" ;
      A52PacienteTelefono = "" ;
      A51PacienteGenero = "" ;
      A46PacienteApMat = "" ;
      A45PacienteApPat = "" ;
      A44PacienteNombre = "" ;
      IMSSOFFLIN11_A317DFFormDsc = new String[] {""} ;
      IMSSOFFLIN11_A303DFFormIsSD = new boolean[] {false} ;
      IMSSOFFLIN11_A159DFFormRunDLT = new boolean[] {false} ;
      IMSSOFFLIN11_A236DFFormHelpURL = new String[] {""} ;
      IMSSOFFLIN11_A176DFFormPrefix = new String[] {""} ;
      IMSSOFFLIN11_A235DFFormPmtHgh = new int[1] ;
      IMSSOFFLIN11_n235DFFormPmtHgh = new boolean[] {false} ;
      IMSSOFFLIN11_A234DFFormPmtWth = new int[1] ;
      IMSSOFFLIN11_n234DFFormPmtWth = new boolean[] {false} ;
      IMSSOFFLIN11_A237DFFormAct = new boolean[] {false} ;
      IMSSOFFLIN11_A171DFFormName = new String[] {""} ;
      IMSSOFFLIN11_A115DFFormGuid = new java.util.UUID[] {java.util.UUID.fromString("00000000-0000-0000-0000-000000000000")} ;
      IMSSOFFLIN11_A87DFFormVer = new int[1] ;
      IMSSOFFLIN11_A86DFFormId = new int[1] ;
      A317DFFormDsc = "" ;
      A236DFFormHelpURL = "" ;
      A176DFFormPrefix = "" ;
      A171DFFormName = "" ;
      A115DFFormGuid = java.util.UUID.fromString("00000000-0000-0000-0000-000000000000") ;
      IMSSOFFLIN12_A85FormatoPacienteMedicoNombre = new String[] {""} ;
      IMSSOFFLIN12_A84FormatoPacienteMedicoMatricula = new long[1] ;
      IMSSOFFLIN12_A90DFFormInstId = new long[1] ;
      IMSSOFFLIN12_A80FormatoPacienteAgregado = new String[] {""} ;
      IMSSOFFLIN12_A79FormatoPacienteNSS = new String[] {""} ;
      A85FormatoPacienteMedicoNombre = "" ;
      A80FormatoPacienteAgregado = "" ;
      A79FormatoPacienteNSS = "" ;
      IMSSOFFLIN13_A306ExtensionNombre = new String[] {""} ;
      IMSSOFFLIN13_A305ExtensionTipo = new short[1] ;
      IMSSOFFLIN13_A304ExtensionId = new short[1] ;
      A306ExtensionNombre = "" ;
      IMSSOFFLIN14_A313DFElemFormReq = new boolean[] {false} ;
      IMSSOFFLIN14_A316DFElemFormPrtPic = new String[] {""} ;
      IMSSOFFLIN14_A307DFElemFormLoadRule = new String[] {""} ;
      IMSSOFFLIN14_n307DFElemFormLoadRule = new boolean[] {false} ;
      IMSSOFFLIN14_A266DFElemFormMetadata = new String[] {""} ;
      IMSSOFFLIN14_n266DFElemFormMetadata = new boolean[] {false} ;
      IMSSOFFLIN14_A267DFElemFormShwNbr = new boolean[] {false} ;
      IMSSOFFLIN14_n267DFElemFormShwNbr = new boolean[] {false} ;
      IMSSOFFLIN14_A265DFElemFormDateSel = new boolean[] {false} ;
      IMSSOFFLIN14_n265DFElemFormDateSel = new boolean[] {false} ;
      IMSSOFFLIN14_A262DFElemFormHasPmpt = new boolean[] {false} ;
      IMSSOFFLIN14_n262DFElemFormHasPmpt = new boolean[] {false} ;
      IMSSOFFLIN14_A187DFElemFormIsFlt = new String[] {""} ;
      IMSSOFFLIN14_n187DFElemFormIsFlt = new boolean[] {false} ;
      IMSSOFFLIN14_A186DFElemFormCmpWth = new String[] {""} ;
      IMSSOFFLIN14_n186DFElemFormCmpWth = new boolean[] {false} ;
      IMSSOFFLIN14_A185DFElemFormLblWth = new String[] {""} ;
      IMSSOFFLIN14_n185DFElemFormLblWth = new boolean[] {false} ;
      IMSSOFFLIN14_A285DFElemFormPrtShwNbr = new boolean[] {false} ;
      IMSSOFFLIN14_A284DFElemFormPrtNumColSkip = new int[1] ;
      IMSSOFFLIN14_A276DFElemFormPrtNumRowSkip = new int[1] ;
      IMSSOFFLIN14_A274DFElemFormPrtAddRows = new boolean[] {false} ;
      IMSSOFFLIN14_A273DFElemFormPrtName = new String[] {""} ;
      IMSSOFFLIN14_A194DFElemFormIsVisPrt = new boolean[] {false} ;
      IMSSOFFLIN14_A193DFElemFormIsVis = new boolean[] {false} ;
      IMSSOFFLIN14_A192DFElemFormIsColap = new boolean[] {false} ;
      IMSSOFFLIN14_A191DFElemFormAllowIns = new boolean[] {false} ;
      IMSSOFFLIN14_n191DFElemFormAllowIns = new boolean[] {false} ;
      IMSSOFFLIN14_A190DFElemFormAllowUpd = new boolean[] {false} ;
      IMSSOFFLIN14_n190DFElemFormAllowUpd = new boolean[] {false} ;
      IMSSOFFLIN14_A189DFElemFormAllowDlt = new boolean[] {false} ;
      IMSSOFFLIN14_n189DFElemFormAllowDlt = new boolean[] {false} ;
      IMSSOFFLIN14_A184DFElemFormInhType = new String[] {""} ;
      IMSSOFFLIN14_A116DFElemFormPos = new int[1] ;
      IMSSOFFLIN14_A188DFElemFormName = new String[] {""} ;
      IMSSOFFLIN14_A89DFElemVer = new int[1] ;
      IMSSOFFLIN14_A88DFElemId = new int[1] ;
      IMSSOFFLIN14_A87DFFormVer = new int[1] ;
      IMSSOFFLIN14_A86DFFormId = new int[1] ;
      A316DFElemFormPrtPic = "" ;
      A307DFElemFormLoadRule = "" ;
      A266DFElemFormMetadata = "" ;
      A187DFElemFormIsFlt = "" ;
      A186DFElemFormCmpWth = "" ;
      A185DFElemFormLblWth = "" ;
      A273DFElemFormPrtName = "" ;
      A184DFElemFormInhType = "" ;
      A188DFElemFormName = "" ;
      IMSSOFFLIN15_A147DFElemFormInstFileName = new String[] {""} ;
      IMSSOFFLIN15_n147DFElemFormInstFileName = new boolean[] {false} ;
      IMSSOFFLIN15_A146DFElemFormInstFileType = new String[] {""} ;
      IMSSOFFLIN15_n146DFElemFormInstFileType = new boolean[] {false} ;
      IMSSOFFLIN15_A145DFElemFormInstBlob = new String[] {""} ;
      IMSSOFFLIN15_n145DFElemFormInstBlob = new boolean[] {false} ;
      IMSSOFFLIN15_A143DFElemFormInstVal = new String[] {""} ;
      IMSSOFFLIN15_n143DFElemFormInstVal = new boolean[] {false} ;
      IMSSOFFLIN15_A89DFElemVer = new int[1] ;
      IMSSOFFLIN15_A88DFElemId = new int[1] ;
      IMSSOFFLIN15_A90DFFormInstId = new long[1] ;
      A147DFElemFormInstFileName = "" ;
      A146DFElemFormInstFileType = "" ;
      A145DFElemFormInstBlob = "" ;
      A143DFElemFormInstVal = "" ;
      IMSSOFFLIN16_A150DFElemFormInstSubElemFileName = new String[] {""} ;
      IMSSOFFLIN16_n150DFElemFormInstSubElemFileName = new boolean[] {false} ;
      IMSSOFFLIN16_A149DFElemFormInstSubElemFileType = new String[] {""} ;
      IMSSOFFLIN16_n149DFElemFormInstSubElemFileType = new boolean[] {false} ;
      IMSSOFFLIN16_A108DFSubElemFormElemId = new int[1] ;
      IMSSOFFLIN16_A109DFSubElemFormElemVer = new int[1] ;
      IMSSOFFLIN16_A110DFElemFormInstSubElemRow = new int[1] ;
      IMSSOFFLIN16_A144DFElemFormInstSubElemVal = new String[] {""} ;
      IMSSOFFLIN16_n144DFElemFormInstSubElemVal = new boolean[] {false} ;
      IMSSOFFLIN16_A148DFElemFormInstSubElemBlob = new String[] {""} ;
      IMSSOFFLIN16_n148DFElemFormInstSubElemBlob = new boolean[] {false} ;
      IMSSOFFLIN16_A107DFElemFormInstSubElemId = new int[1] ;
      IMSSOFFLIN16_A89DFElemVer = new int[1] ;
      IMSSOFFLIN16_A88DFElemId = new int[1] ;
      IMSSOFFLIN16_A90DFFormInstId = new long[1] ;
      A150DFElemFormInstSubElemFileName = "" ;
      A149DFElemFormInstSubElemFileType = "" ;
      A144DFElemFormInstSubElemVal = "" ;
      A148DFElemFormInstSubElemBlob = "" ;
      IMSSOFFLIN17_A290DFTempFm = new String[] {""} ;
      IMSSOFFLIN17_A287DFTempOutFm = new String[] {""} ;
      IMSSOFFLIN17_A281DFTempAddParmPrgName = new String[] {""} ;
      IMSSOFFLIN17_A280DFTempBlob = new String[] {""} ;
      IMSSOFFLIN17_A286DFTempDsc = new String[] {""} ;
      IMSSOFFLIN17_A136DFTempName = new String[] {""} ;
      IMSSOFFLIN17_A87DFFormVer = new int[1] ;
      IMSSOFFLIN17_A86DFFormId = new int[1] ;
      A290DFTempFm = "" ;
      A287DFTempOutFm = "" ;
      A281DFTempAddParmPrgName = "" ;
      A280DFTempBlob = "" ;
      A286DFTempDsc = "" ;
      A136DFTempName = "" ;
      IMSSOFFLIN18_A225DFDomStaValOptDsc = new String[] {""} ;
      IMSSOFFLIN18_A113DFDomStaValOptOrd = new int[1] ;
      IMSSOFFLIN18_A112DFDomStaValOptCod = new String[] {""} ;
      IMSSOFFLIN18_A111DFDomId = new int[1] ;
      IMSSOFFLIN18_n111DFDomId = new boolean[] {false} ;
      A225DFDomStaValOptDsc = "" ;
      A112DFDomStaValOptCod = "" ;
      IMSSOFFLIN19_A200DFFormInstSignedPDF = new String[] {""} ;
      IMSSOFFLIN19_n200DFFormInstSignedPDF = new boolean[] {false} ;
      IMSSOFFLIN19_A201DFFormInstSignedBy = new String[] {""} ;
      IMSSOFFLIN19_n201DFFormInstSignedBy = new boolean[] {false} ;
      IMSSOFFLIN19_A157DFFormInstDT = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN19_A106DFFormInstFormVer = new int[1] ;
      IMSSOFFLIN19_A105DFFormInstFormId = new int[1] ;
      IMSSOFFLIN19_A90DFFormInstId = new long[1] ;
      A200DFFormInstSignedPDF = "" ;
      A201DFFormInstSignedBy = "" ;
      A157DFFormInstDT = GXutil.resetTime( GXutil.nullDate() );
      IMSSOFFLIN20_A314DFElemReq = new boolean[] {false} ;
      IMSSOFFLIN20_A315DFElemPrtPic = new String[] {""} ;
      IMSSOFFLIN20_A308DFElemLoadRule = new String[] {""} ;
      IMSSOFFLIN20_n308DFElemLoadRule = new boolean[] {false} ;
      IMSSOFFLIN20_A268DFElemMetadata = new String[] {""} ;
      IMSSOFFLIN20_n268DFElemMetadata = new boolean[] {false} ;
      IMSSOFFLIN20_A241DFElemIsColap = new boolean[] {false} ;
      IMSSOFFLIN20_A283DFElemPrtShwNbr = new boolean[] {false} ;
      IMSSOFFLIN20_A282DFElemPrtNumColSkip = new int[1] ;
      IMSSOFFLIN20_A277DFElemPrtNumRowSkip = new int[1] ;
      IMSSOFFLIN20_A275DFElemPrtAddRows = new boolean[] {false} ;
      IMSSOFFLIN20_A272DFElemPrtName = new String[] {""} ;
      IMSSOFFLIN20_A263DFElemIsVisPrt = new boolean[] {false} ;
      IMSSOFFLIN20_A240DFElemIsVis = new boolean[] {false} ;
      IMSSOFFLIN20_A260DFElemLblWth = new String[] {""} ;
      IMSSOFFLIN20_n260DFElemLblWth = new boolean[] {false} ;
      IMSSOFFLIN20_A246DFElemCmpWth = new String[] {""} ;
      IMSSOFFLIN20_n246DFElemCmpWth = new boolean[] {false} ;
      IMSSOFFLIN20_A245DFElemIsFlt = new String[] {""} ;
      IMSSOFFLIN20_n245DFElemIsFlt = new boolean[] {false} ;
      IMSSOFFLIN20_A259DFElemFileType = new String[] {""} ;
      IMSSOFFLIN20_n259DFElemFileType = new boolean[] {false} ;
      IMSSOFFLIN20_A257DFElemRegexVal = new String[] {""} ;
      IMSSOFFLIN20_n257DFElemRegexVal = new boolean[] {false} ;
      IMSSOFFLIN20_A256DFElemAllowDlt = new boolean[] {false} ;
      IMSSOFFLIN20_n256DFElemAllowDlt = new boolean[] {false} ;
      IMSSOFFLIN20_A255DFElemAllowUpd = new boolean[] {false} ;
      IMSSOFFLIN20_n255DFElemAllowUpd = new boolean[] {false} ;
      IMSSOFFLIN20_A254DFElemAllowIns = new boolean[] {false} ;
      IMSSOFFLIN20_n254DFElemAllowIns = new boolean[] {false} ;
      IMSSOFFLIN20_A253DFElemUseBtns = new boolean[] {false} ;
      IMSSOFFLIN20_n253DFElemUseBtns = new boolean[] {false} ;
      IMSSOFFLIN20_A252DFElemIsOrd = new boolean[] {false} ;
      IMSSOFFLIN20_n252DFElemIsOrd = new boolean[] {false} ;
      IMSSOFFLIN20_A251DFElemMaxSuggRes = new int[1] ;
      IMSSOFFLIN20_n251DFElemMaxSuggRes = new boolean[] {false} ;
      IMSSOFFLIN20_A250DFElemForceSuggSel = new boolean[] {false} ;
      IMSSOFFLIN20_n250DFElemForceSuggSel = new boolean[] {false} ;
      IMSSOFFLIN20_A249DFElemMinCntCharSugg = new int[1] ;
      IMSSOFFLIN20_n249DFElemMinCntCharSugg = new boolean[] {false} ;
      IMSSOFFLIN20_A261DFElemDscPrgName = new String[] {""} ;
      IMSSOFFLIN20_A248DFElemLoadPrgName = new String[] {""} ;
      IMSSOFFLIN20_n248DFElemLoadPrgName = new boolean[] {false} ;
      IMSSOFFLIN20_A270DFElemBtnPos = new String[] {""} ;
      IMSSOFFLIN20_n270DFElemBtnPos = new boolean[] {false} ;
      IMSSOFFLIN20_A271DFElemShwNbrLbl = new String[] {""} ;
      IMSSOFFLIN20_n271DFElemShwNbrLbl = new boolean[] {false} ;
      IMSSOFFLIN20_A269DFElemShwNbr = new boolean[] {false} ;
      IMSSOFFLIN20_n269DFElemShwNbr = new boolean[] {false} ;
      IMSSOFFLIN20_A264DFElemDateSel = new boolean[] {false} ;
      IMSSOFFLIN20_n264DFElemDateSel = new boolean[] {false} ;
      IMSSOFFLIN20_A247DFElemHasPmpt = new boolean[] {false} ;
      IMSSOFFLIN20_n247DFElemHasPmpt = new boolean[] {false} ;
      IMSSOFFLIN20_A183DFElemDftVal = new String[] {""} ;
      IMSSOFFLIN20_n183DFElemDftVal = new boolean[] {false} ;
      IMSSOFFLIN20_A244DFElemCntCols = new int[1] ;
      IMSSOFFLIN20_n244DFElemCntCols = new boolean[] {false} ;
      IMSSOFFLIN20_A243DFElemCntRows = new int[1] ;
      IMSSOFFLIN20_n243DFElemCntRows = new boolean[] {false} ;
      IMSSOFFLIN20_A242DFElemCntDec = new int[1] ;
      IMSSOFFLIN20_n242DFElemCntDec = new boolean[] {false} ;
      IMSSOFFLIN20_A258DFElemWth = new int[1] ;
      IMSSOFFLIN20_n258DFElemWth = new boolean[] {false} ;
      IMSSOFFLIN20_A239DFElemLen = new int[1] ;
      IMSSOFFLIN20_n239DFElemLen = new boolean[] {false} ;
      IMSSOFFLIN20_A199DFElemDsp = new String[] {""} ;
      IMSSOFFLIN20_n199DFElemDsp = new boolean[] {false} ;
      IMSSOFFLIN20_A181DFElemType = new String[] {""} ;
      IMSSOFFLIN20_A111DFDomId = new int[1] ;
      IMSSOFFLIN20_n111DFDomId = new boolean[] {false} ;
      IMSSOFFLIN20_A195DFElemClsName = new String[] {""} ;
      IMSSOFFLIN20_n195DFElemClsName = new boolean[] {false} ;
      IMSSOFFLIN20_A238DFElemDsc = new String[] {""} ;
      IMSSOFFLIN20_n238DFElemDsc = new boolean[] {false} ;
      IMSSOFFLIN20_A151DFElemName = new String[] {""} ;
      IMSSOFFLIN20_A114DFElemGuid = new java.util.UUID[] {java.util.UUID.fromString("00000000-0000-0000-0000-000000000000")} ;
      IMSSOFFLIN20_A89DFElemVer = new int[1] ;
      IMSSOFFLIN20_A88DFElemId = new int[1] ;
      A315DFElemPrtPic = "" ;
      A308DFElemLoadRule = "" ;
      A268DFElemMetadata = "" ;
      A272DFElemPrtName = "" ;
      A260DFElemLblWth = "" ;
      A246DFElemCmpWth = "" ;
      A245DFElemIsFlt = "" ;
      A259DFElemFileType = "" ;
      A257DFElemRegexVal = "" ;
      A261DFElemDscPrgName = "" ;
      A248DFElemLoadPrgName = "" ;
      A270DFElemBtnPos = "" ;
      A271DFElemShwNbrLbl = "" ;
      A183DFElemDftVal = "" ;
      A199DFElemDsp = "" ;
      A181DFElemType = "" ;
      A195DFElemClsName = "" ;
      A238DFElemDsc = "" ;
      A151DFElemName = "" ;
      A114DFElemGuid = java.util.UUID.fromString("00000000-0000-0000-0000-000000000000") ;
      IMSSOFFLIN21_A93DFFormRstVal = new String[] {""} ;
      IMSSOFFLIN21_A92DFFormRstId = new int[1] ;
      IMSSOFFLIN21_A87DFFormVer = new int[1] ;
      IMSSOFFLIN21_A86DFFormId = new int[1] ;
      A93DFFormRstVal = "" ;
      IMSSOFFLIN22_A166DFUserRstPwdIni = new boolean[] {false} ;
      IMSSOFFLIN22_A101DFUserRstVal = new String[] {""} ;
      IMSSOFFLIN22_A100DFUserRstId = new int[1] ;
      IMSSOFFLIN22_A99DFUserExtId = new String[] {""} ;
      A101DFUserRstVal = "" ;
      A99DFUserExtId = "" ;
      IMSSOFFLIN23_A319DFDomPrtDsc = new boolean[] {false} ;
      IMSSOFFLIN23_n319DFDomPrtDsc = new boolean[] {false} ;
      IMSSOFFLIN23_A226DFDomLblWth = new String[] {""} ;
      IMSSOFFLIN23_n226DFDomLblWth = new boolean[] {false} ;
      IMSSOFFLIN23_A222DFDomCmpWth = new String[] {""} ;
      IMSSOFFLIN23_n222DFDomCmpWth = new boolean[] {false} ;
      IMSSOFFLIN23_A221DFDomIsFlt = new String[] {""} ;
      IMSSOFFLIN23_n221DFDomIsFlt = new boolean[] {false} ;
      IMSSOFFLIN23_A224DFDomFileType = new String[] {""} ;
      IMSSOFFLIN23_n224DFDomFileType = new boolean[] {false} ;
      IMSSOFFLIN23_A220DFDomRegexVal = new String[] {""} ;
      IMSSOFFLIN23_A216DFDomAllowDlt = new boolean[] {false} ;
      IMSSOFFLIN23_n216DFDomAllowDlt = new boolean[] {false} ;
      IMSSOFFLIN23_A215DFDomAllowUpd = new boolean[] {false} ;
      IMSSOFFLIN23_n215DFDomAllowUpd = new boolean[] {false} ;
      IMSSOFFLIN23_A214DFDomAllowIns = new boolean[] {false} ;
      IMSSOFFLIN23_n214DFDomAllowIns = new boolean[] {false} ;
      IMSSOFFLIN23_A213DFDomUseBtns = new boolean[] {false} ;
      IMSSOFFLIN23_n213DFDomUseBtns = new boolean[] {false} ;
      IMSSOFFLIN23_A212DFDomIsOrd = new boolean[] {false} ;
      IMSSOFFLIN23_n212DFDomIsOrd = new boolean[] {false} ;
      IMSSOFFLIN23_A210DFDomMaxSuggRes = new int[1] ;
      IMSSOFFLIN23_n210DFDomMaxSuggRes = new boolean[] {false} ;
      IMSSOFFLIN23_A209DFDomForceSuggSel = new boolean[] {false} ;
      IMSSOFFLIN23_n209DFDomForceSuggSel = new boolean[] {false} ;
      IMSSOFFLIN23_A208DFDomMinCntCharSugg = new int[1] ;
      IMSSOFFLIN23_n208DFDomMinCntCharSugg = new boolean[] {false} ;
      IMSSOFFLIN23_A211DFDomDftVal = new String[] {""} ;
      IMSSOFFLIN23_n211DFDomDftVal = new boolean[] {false} ;
      IMSSOFFLIN23_A219DFDomCntCols = new int[1] ;
      IMSSOFFLIN23_A218DFDomCntRows = new int[1] ;
      IMSSOFFLIN23_A217DFDomCntDec = new int[1] ;
      IMSSOFFLIN23_A223DFDomWth = new int[1] ;
      IMSSOFFLIN23_A207DFDomLen = new int[1] ;
      IMSSOFFLIN23_A198DFDomDsp = new String[] {""} ;
      IMSSOFFLIN23_n198DFDomDsp = new boolean[] {false} ;
      IMSSOFFLIN23_A197DFDomType = new String[] {""} ;
      IMSSOFFLIN23_A227DFDomGUID = new java.util.UUID[] {java.util.UUID.fromString("00000000-0000-0000-0000-000000000000")} ;
      IMSSOFFLIN23_A206DFDomDsc = new String[] {""} ;
      IMSSOFFLIN23_A111DFDomId = new int[1] ;
      IMSSOFFLIN23_n111DFDomId = new boolean[] {false} ;
      A226DFDomLblWth = "" ;
      A222DFDomCmpWth = "" ;
      A221DFDomIsFlt = "" ;
      A224DFDomFileType = "" ;
      A220DFDomRegexVal = "" ;
      A211DFDomDftVal = "" ;
      A198DFDomDsp = "" ;
      A197DFDomType = "" ;
      A227DFDomGUID = java.util.UUID.fromString("00000000-0000-0000-0000-000000000000") ;
      A206DFDomDsc = "" ;
      IMSSOFFLIN24_A117DFSubElemFormPos = new int[1] ;
      IMSSOFFLIN24_n117DFSubElemFormPos = new boolean[] {false} ;
      IMSSOFFLIN24_A109DFSubElemFormElemVer = new int[1] ;
      IMSSOFFLIN24_A108DFSubElemFormElemId = new int[1] ;
      IMSSOFFLIN24_A89DFElemVer = new int[1] ;
      IMSSOFFLIN24_A88DFElemId = new int[1] ;
      IMSSOFFLIN24_A87DFFormVer = new int[1] ;
      IMSSOFFLIN24_A86DFFormId = new int[1] ;
      IMSSOFFLIN25_A120DFFilElemFormElemVer = new int[1] ;
      IMSSOFFLIN25_A119DFFilElemFormElemId = new int[1] ;
      IMSSOFFLIN25_A121DFFilElemFormPos = new short[1] ;
      IMSSOFFLIN25_A118DFFilElemFormId = new int[1] ;
      IMSSOFFLIN25_A89DFElemVer = new int[1] ;
      IMSSOFFLIN25_A88DFElemId = new int[1] ;
      IMSSOFFLIN25_A87DFFormVer = new int[1] ;
      IMSSOFFLIN25_A86DFFormId = new int[1] ;
      IMSSOFFLIN26_A288HospitalId = new short[1] ;
      IMSSOFFLIN26_n288HospitalId = new boolean[] {false} ;
      IMSSOFFLIN26_A36ServicioDescripcion = new String[] {""} ;
      IMSSOFFLIN26_A6ServicioId = new short[1] ;
      A36ServicioDescripcion = "" ;
      IMSSOFFLIN27_A105DFFormInstFormId = new int[1] ;
      IMSSOFFLIN27_A141DFUplFileExt = new String[] {""} ;
      IMSSOFFLIN27_A142DFUplFileName = new String[] {""} ;
      IMSSOFFLIN27_A140DFUplFile = new String[] {""} ;
      IMSSOFFLIN27_A91DFUplKey = new String[] {""} ;
      IMSSOFFLIN27_A90DFFormInstId = new long[1] ;
      A141DFUplFileExt = "" ;
      A142DFUplFileName = "" ;
      A140DFUplFile = "" ;
      A91DFUplKey = "" ;
      GXv_objcol_gxjsonable7 = new com.genexus.GxUnknownObjectCollection [1] ;
      GXv_objcol_gxjsonable6 = new com.genexus.GxUnknownObjectCollection [1] ;
      GXv_objcol_gxjsonable5 = new com.genexus.GxUnknownObjectCollection [1] ;
      GXv_int8 = new short [1] ;
      gxallsyncresponse = new com.genexus.GxUnknownObjectCollection();
      gxsyncheaderline = new com.genexus.internet.StringCollection();
      gxsourcever = "" ;
      gxhttpr = httpContext.getHttpRequest();
      gxtableheadlist = new com.genexus.GxUnknownObjectCollection();
      DEVICEID = "" ;
      QUERYID = "" ;
      RESULTSET = "" ;
      pr_default = new DataStoreProvider(context, remoteHandle, new com.imss.imssofflinedatabase__default(),
         new Object[] {
             new Object[] {
            IMSSOFFLIN2_A312MedicoDebeMostarTerm, IMSSOFFLIN2_A302MedicoDebeValidarDatos, IMSSOFFLIN2_A300MedicoUltimaActualizacion, IMSSOFFLIN2_A297MedicoMatricula, IMSSOFFLIN2_n297MedicoMatricula, IMSSOFFLIN2_A296MedicoApellidoMaterno, IMSSOFFLIN2_A295MedicoApellidoPaterno, IMSSOFFLIN2_A294MedicoSegundoNombre, IMSSOFFLIN2_A293MedicoPrimerNombre, IMSSOFFLIN2_A292UserMedico
            }
            , new Object[] {
            IMSSOFFLIN3_A75PacienteNSSAgregado, IMSSOFFLIN3_A81Matricula, IMSSOFFLIN3_A3PacienteAgregado, IMSSOFFLIN3_A2PacienteNSS
            }
            , new Object[] {
            IMSSOFFLIN4_A69CIECodigo, IMSSOFFLIN4_A10CIE10Descripcion, IMSSOFFLIN4_A1CIE10Id
            }
            , new Object[] {
            IMSSOFFLIN5_A75PacienteNSSAgregado, IMSSOFFLIN5_A34MMatricula, IMSSOFFLIN5_n34MMatricula, IMSSOFFLIN5_A33MApMat, IMSSOFFLIN5_n33MApMat, IMSSOFFLIN5_A32MApPat, IMSSOFFLIN5_n32MApPat, IMSSOFFLIN5_A31MNombre, IMSSOFFLIN5_n31MNombre, IMSSOFFLIN5_A30MBMatricula,
            IMSSOFFLIN5_n30MBMatricula, IMSSOFFLIN5_A29MBApMat, IMSSOFFLIN5_n29MBApMat, IMSSOFFLIN5_A28MBApPat, IMSSOFFLIN5_n28MBApPat, IMSSOFFLIN5_A27MBNombre, IMSSOFFLIN5_n27MBNombre, IMSSOFFLIN5_A26JSMatricula, IMSSOFFLIN5_n26JSMatricula, IMSSOFFLIN5_A25JSApMat,
            IMSSOFFLIN5_n25JSApMat, IMSSOFFLIN5_A24JSApPat, IMSSOFFLIN5_n24JSApPat, IMSSOFFLIN5_A23JSNombre, IMSSOFFLIN5_n23JSNombre, IMSSOFFLIN5_A22DiagnosticoCirugiaFecha, IMSSOFFLIN5_n22DiagnosticoCirugiaFecha, IMSSOFFLIN5_A21DiagnosticoCirugia, IMSSOFFLIN5_n21DiagnosticoCirugia, IMSSOFFLIN5_A20Cama,
            IMSSOFFLIN5_n20Cama, IMSSOFFLIN5_A6ServicioId, IMSSOFFLIN5_A19DiagnosticoResumen, IMSSOFFLIN5_n19DiagnosticoResumen, IMSSOFFLIN5_A18DiagnosticoComplemento, IMSSOFFLIN5_n18DiagnosticoComplemento, IMSSOFFLIN5_A35DiagnosticoFechaAlta, IMSSOFFLIN5_n35DiagnosticoFechaAlta, IMSSOFFLIN5_A17DiagnosticoFechaIngreso, IMSSOFFLIN5_n17DiagnosticoFechaIngreso,
            IMSSOFFLIN5_A1CIE10Id, IMSSOFFLIN5_A3PacienteAgregado, IMSSOFFLIN5_A2PacienteNSS
            }
            , new Object[] {
            IMSSOFFLIN6_A323nada, IMSSOFFLIN6_A311TextoDescripcion, IMSSOFFLIN6_A310TextoTitulo, IMSSOFFLIN6_A309TextoId
            }
            , new Object[] {
            IMSSOFFLIN7_A169DFParmIsMetaData, IMSSOFFLIN7_A168DFParmVal, IMSSOFFLIN7_A167DFParmName, IMSSOFFLIN7_A102DFParmId
            }
            , new Object[] {
            IMSSOFFLIN8_A75PacienteNSSAgregado, IMSSOFFLIN8_A40000DXAuxImagenImg_GXI, IMSSOFFLIN8_A322DXAuxImagenExtension, IMSSOFFLIN8_A73DXAuxImagenNombre, IMSSOFFLIN8_A16DXAuxImagenUserAlta, IMSSOFFLIN8_A15DXAuxImagenFechaAlta, IMSSOFFLIN8_A14DXAuxImagenImg, IMSSOFFLIN8_A5DXAuxImagenId, IMSSOFFLIN8_A1CIE10Id, IMSSOFFLIN8_A3PacienteAgregado,
            IMSSOFFLIN8_A2PacienteNSS
            }
            , new Object[] {
            IMSSOFFLIN9_A75PacienteNSSAgregado, IMSSOFFLIN9_A74DXAuxDoctoNombre, IMSSOFFLIN9_A82DXAuxDoctoExtension, IMSSOFFLIN9_A13DXAuxDoctoUserAlta, IMSSOFFLIN9_A12DXAuxDoctoFechaAlta, IMSSOFFLIN9_A11DXAuxDoctoDocumento, IMSSOFFLIN9_A4DXAuxDoctoId, IMSSOFFLIN9_A1CIE10Id, IMSSOFFLIN9_A3PacienteAgregado, IMSSOFFLIN9_A2PacienteNSS
            }
            , new Object[] {
            IMSSOFFLIN10_A321PacienteServicioId, IMSSOFFLIN10_A298PacienteDiagnosticoPhone, IMSSOFFLIN10_A291PacienteCie10Id, IMSSOFFLIN10_A76PAcienteFechaIngreso, IMSSOFFLIN10_A75PacienteNSSAgregado, IMSSOFFLIN10_A72PacienteCama, IMSSOFFLIN10_A71PacienteDiagnosticoResumido, IMSSOFFLIN10_A70PacienteDiagnostico, IMSSOFFLIN10_A68PacienteFechaNacimiento, IMSSOFFLIN10_A55PacienteNombreCompleto,
            IMSSOFFLIN10_A54PacienteReferencia, IMSSOFFLIN10_n54PacienteReferencia, IMSSOFFLIN10_A53PacienteFamiliar, IMSSOFFLIN10_n53PacienteFamiliar, IMSSOFFLIN10_A52PacienteTelefono, IMSSOFFLIN10_n52PacienteTelefono, IMSSOFFLIN10_A51PacienteGenero, IMSSOFFLIN10_n51PacienteGenero, IMSSOFFLIN10_A50PacienteEdad, IMSSOFFLIN10_A46PacienteApMat,
            IMSSOFFLIN10_n46PacienteApMat, IMSSOFFLIN10_A45PacienteApPat, IMSSOFFLIN10_A44PacienteNombre, IMSSOFFLIN10_A3PacienteAgregado, IMSSOFFLIN10_A2PacienteNSS
            }
            , new Object[] {
            IMSSOFFLIN11_A317DFFormDsc, IMSSOFFLIN11_A303DFFormIsSD, IMSSOFFLIN11_A159DFFormRunDLT, IMSSOFFLIN11_A236DFFormHelpURL, IMSSOFFLIN11_A176DFFormPrefix, IMSSOFFLIN11_A235DFFormPmtHgh, IMSSOFFLIN11_n235DFFormPmtHgh, IMSSOFFLIN11_A234DFFormPmtWth, IMSSOFFLIN11_n234DFFormPmtWth, IMSSOFFLIN11_A237DFFormAct,
            IMSSOFFLIN11_A171DFFormName, IMSSOFFLIN11_A115DFFormGuid, IMSSOFFLIN11_A87DFFormVer, IMSSOFFLIN11_A86DFFormId
            }
            , new Object[] {
            IMSSOFFLIN12_A85FormatoPacienteMedicoNombre, IMSSOFFLIN12_A84FormatoPacienteMedicoMatricula, IMSSOFFLIN12_A90DFFormInstId, IMSSOFFLIN12_A80FormatoPacienteAgregado, IMSSOFFLIN12_A79FormatoPacienteNSS
            }
            , new Object[] {
            IMSSOFFLIN13_A306ExtensionNombre, IMSSOFFLIN13_A305ExtensionTipo, IMSSOFFLIN13_A304ExtensionId
            }
            , new Object[] {
            IMSSOFFLIN14_A313DFElemFormReq, IMSSOFFLIN14_A316DFElemFormPrtPic, IMSSOFFLIN14_A307DFElemFormLoadRule, IMSSOFFLIN14_n307DFElemFormLoadRule, IMSSOFFLIN14_A266DFElemFormMetadata, IMSSOFFLIN14_n266DFElemFormMetadata, IMSSOFFLIN14_A267DFElemFormShwNbr, IMSSOFFLIN14_n267DFElemFormShwNbr, IMSSOFFLIN14_A265DFElemFormDateSel, IMSSOFFLIN14_n265DFElemFormDateSel,
            IMSSOFFLIN14_A262DFElemFormHasPmpt, IMSSOFFLIN14_n262DFElemFormHasPmpt, IMSSOFFLIN14_A187DFElemFormIsFlt, IMSSOFFLIN14_n187DFElemFormIsFlt, IMSSOFFLIN14_A186DFElemFormCmpWth, IMSSOFFLIN14_n186DFElemFormCmpWth, IMSSOFFLIN14_A185DFElemFormLblWth, IMSSOFFLIN14_n185DFElemFormLblWth, IMSSOFFLIN14_A285DFElemFormPrtShwNbr, IMSSOFFLIN14_A284DFElemFormPrtNumColSkip,
            IMSSOFFLIN14_A276DFElemFormPrtNumRowSkip, IMSSOFFLIN14_A274DFElemFormPrtAddRows, IMSSOFFLIN14_A273DFElemFormPrtName, IMSSOFFLIN14_A194DFElemFormIsVisPrt, IMSSOFFLIN14_A193DFElemFormIsVis, IMSSOFFLIN14_A192DFElemFormIsColap, IMSSOFFLIN14_A191DFElemFormAllowIns, IMSSOFFLIN14_n191DFElemFormAllowIns, IMSSOFFLIN14_A190DFElemFormAllowUpd, IMSSOFFLIN14_n190DFElemFormAllowUpd,
            IMSSOFFLIN14_A189DFElemFormAllowDlt, IMSSOFFLIN14_n189DFElemFormAllowDlt, IMSSOFFLIN14_A184DFElemFormInhType, IMSSOFFLIN14_A116DFElemFormPos, IMSSOFFLIN14_A188DFElemFormName, IMSSOFFLIN14_A89DFElemVer, IMSSOFFLIN14_A88DFElemId, IMSSOFFLIN14_A87DFFormVer, IMSSOFFLIN14_A86DFFormId
            }
            , new Object[] {
            IMSSOFFLIN15_A147DFElemFormInstFileName, IMSSOFFLIN15_n147DFElemFormInstFileName, IMSSOFFLIN15_A146DFElemFormInstFileType, IMSSOFFLIN15_n146DFElemFormInstFileType, IMSSOFFLIN15_A145DFElemFormInstBlob, IMSSOFFLIN15_n145DFElemFormInstBlob, IMSSOFFLIN15_A143DFElemFormInstVal, IMSSOFFLIN15_n143DFElemFormInstVal, IMSSOFFLIN15_A89DFElemVer, IMSSOFFLIN15_A88DFElemId,
            IMSSOFFLIN15_A90DFFormInstId
            }
            , new Object[] {
            IMSSOFFLIN16_A150DFElemFormInstSubElemFileName, IMSSOFFLIN16_n150DFElemFormInstSubElemFileName, IMSSOFFLIN16_A149DFElemFormInstSubElemFileType, IMSSOFFLIN16_n149DFElemFormInstSubElemFileType, IMSSOFFLIN16_A108DFSubElemFormElemId, IMSSOFFLIN16_A109DFSubElemFormElemVer, IMSSOFFLIN16_A110DFElemFormInstSubElemRow, IMSSOFFLIN16_A144DFElemFormInstSubElemVal, IMSSOFFLIN16_n144DFElemFormInstSubElemVal, IMSSOFFLIN16_A148DFElemFormInstSubElemBlob,
            IMSSOFFLIN16_n148DFElemFormInstSubElemBlob, IMSSOFFLIN16_A107DFElemFormInstSubElemId, IMSSOFFLIN16_A89DFElemVer, IMSSOFFLIN16_A88DFElemId, IMSSOFFLIN16_A90DFFormInstId
            }
            , new Object[] {
            IMSSOFFLIN17_A290DFTempFm, IMSSOFFLIN17_A287DFTempOutFm, IMSSOFFLIN17_A281DFTempAddParmPrgName, IMSSOFFLIN17_A280DFTempBlob, IMSSOFFLIN17_A286DFTempDsc, IMSSOFFLIN17_A136DFTempName, IMSSOFFLIN17_A87DFFormVer, IMSSOFFLIN17_A86DFFormId
            }
            , new Object[] {
            IMSSOFFLIN18_A225DFDomStaValOptDsc, IMSSOFFLIN18_A113DFDomStaValOptOrd, IMSSOFFLIN18_A112DFDomStaValOptCod, IMSSOFFLIN18_A111DFDomId
            }
            , new Object[] {
            IMSSOFFLIN19_A200DFFormInstSignedPDF, IMSSOFFLIN19_n200DFFormInstSignedPDF, IMSSOFFLIN19_A201DFFormInstSignedBy, IMSSOFFLIN19_n201DFFormInstSignedBy, IMSSOFFLIN19_A157DFFormInstDT, IMSSOFFLIN19_A106DFFormInstFormVer, IMSSOFFLIN19_A105DFFormInstFormId, IMSSOFFLIN19_A90DFFormInstId
            }
            , new Object[] {
            IMSSOFFLIN20_A314DFElemReq, IMSSOFFLIN20_A315DFElemPrtPic, IMSSOFFLIN20_A308DFElemLoadRule, IMSSOFFLIN20_n308DFElemLoadRule, IMSSOFFLIN20_A268DFElemMetadata, IMSSOFFLIN20_n268DFElemMetadata, IMSSOFFLIN20_A241DFElemIsColap, IMSSOFFLIN20_A283DFElemPrtShwNbr, IMSSOFFLIN20_A282DFElemPrtNumColSkip, IMSSOFFLIN20_A277DFElemPrtNumRowSkip,
            IMSSOFFLIN20_A275DFElemPrtAddRows, IMSSOFFLIN20_A272DFElemPrtName, IMSSOFFLIN20_A263DFElemIsVisPrt, IMSSOFFLIN20_A240DFElemIsVis, IMSSOFFLIN20_A260DFElemLblWth, IMSSOFFLIN20_n260DFElemLblWth, IMSSOFFLIN20_A246DFElemCmpWth, IMSSOFFLIN20_n246DFElemCmpWth, IMSSOFFLIN20_A245DFElemIsFlt, IMSSOFFLIN20_n245DFElemIsFlt,
            IMSSOFFLIN20_A259DFElemFileType, IMSSOFFLIN20_n259DFElemFileType, IMSSOFFLIN20_A257DFElemRegexVal, IMSSOFFLIN20_n257DFElemRegexVal, IMSSOFFLIN20_A256DFElemAllowDlt, IMSSOFFLIN20_n256DFElemAllowDlt, IMSSOFFLIN20_A255DFElemAllowUpd, IMSSOFFLIN20_n255DFElemAllowUpd, IMSSOFFLIN20_A254DFElemAllowIns, IMSSOFFLIN20_n254DFElemAllowIns,
            IMSSOFFLIN20_A253DFElemUseBtns, IMSSOFFLIN20_n253DFElemUseBtns, IMSSOFFLIN20_A252DFElemIsOrd, IMSSOFFLIN20_n252DFElemIsOrd, IMSSOFFLIN20_A251DFElemMaxSuggRes, IMSSOFFLIN20_n251DFElemMaxSuggRes, IMSSOFFLIN20_A250DFElemForceSuggSel, IMSSOFFLIN20_n250DFElemForceSuggSel, IMSSOFFLIN20_A249DFElemMinCntCharSugg, IMSSOFFLIN20_n249DFElemMinCntCharSugg,
            IMSSOFFLIN20_A261DFElemDscPrgName, IMSSOFFLIN20_A248DFElemLoadPrgName, IMSSOFFLIN20_n248DFElemLoadPrgName, IMSSOFFLIN20_A270DFElemBtnPos, IMSSOFFLIN20_n270DFElemBtnPos, IMSSOFFLIN20_A271DFElemShwNbrLbl, IMSSOFFLIN20_n271DFElemShwNbrLbl, IMSSOFFLIN20_A269DFElemShwNbr, IMSSOFFLIN20_n269DFElemShwNbr, IMSSOFFLIN20_A264DFElemDateSel,
            IMSSOFFLIN20_n264DFElemDateSel, IMSSOFFLIN20_A247DFElemHasPmpt, IMSSOFFLIN20_n247DFElemHasPmpt, IMSSOFFLIN20_A183DFElemDftVal, IMSSOFFLIN20_n183DFElemDftVal, IMSSOFFLIN20_A244DFElemCntCols, IMSSOFFLIN20_n244DFElemCntCols, IMSSOFFLIN20_A243DFElemCntRows, IMSSOFFLIN20_n243DFElemCntRows, IMSSOFFLIN20_A242DFElemCntDec,
            IMSSOFFLIN20_n242DFElemCntDec, IMSSOFFLIN20_A258DFElemWth, IMSSOFFLIN20_n258DFElemWth, IMSSOFFLIN20_A239DFElemLen, IMSSOFFLIN20_n239DFElemLen, IMSSOFFLIN20_A199DFElemDsp, IMSSOFFLIN20_n199DFElemDsp, IMSSOFFLIN20_A181DFElemType, IMSSOFFLIN20_A111DFDomId, IMSSOFFLIN20_n111DFDomId,
            IMSSOFFLIN20_A195DFElemClsName, IMSSOFFLIN20_n195DFElemClsName, IMSSOFFLIN20_A238DFElemDsc, IMSSOFFLIN20_n238DFElemDsc, IMSSOFFLIN20_A151DFElemName, IMSSOFFLIN20_A114DFElemGuid, IMSSOFFLIN20_A89DFElemVer, IMSSOFFLIN20_A88DFElemId
            }
            , new Object[] {
            IMSSOFFLIN21_A93DFFormRstVal, IMSSOFFLIN21_A92DFFormRstId, IMSSOFFLIN21_A87DFFormVer, IMSSOFFLIN21_A86DFFormId
            }
            , new Object[] {
            IMSSOFFLIN22_A166DFUserRstPwdIni, IMSSOFFLIN22_A101DFUserRstVal, IMSSOFFLIN22_A100DFUserRstId, IMSSOFFLIN22_A99DFUserExtId
            }
            , new Object[] {
            IMSSOFFLIN23_A319DFDomPrtDsc, IMSSOFFLIN23_n319DFDomPrtDsc, IMSSOFFLIN23_A226DFDomLblWth, IMSSOFFLIN23_n226DFDomLblWth, IMSSOFFLIN23_A222DFDomCmpWth, IMSSOFFLIN23_n222DFDomCmpWth, IMSSOFFLIN23_A221DFDomIsFlt, IMSSOFFLIN23_n221DFDomIsFlt, IMSSOFFLIN23_A224DFDomFileType, IMSSOFFLIN23_n224DFDomFileType,
            IMSSOFFLIN23_A220DFDomRegexVal, IMSSOFFLIN23_A216DFDomAllowDlt, IMSSOFFLIN23_n216DFDomAllowDlt, IMSSOFFLIN23_A215DFDomAllowUpd, IMSSOFFLIN23_n215DFDomAllowUpd, IMSSOFFLIN23_A214DFDomAllowIns, IMSSOFFLIN23_n214DFDomAllowIns, IMSSOFFLIN23_A213DFDomUseBtns, IMSSOFFLIN23_n213DFDomUseBtns, IMSSOFFLIN23_A212DFDomIsOrd,
            IMSSOFFLIN23_n212DFDomIsOrd, IMSSOFFLIN23_A210DFDomMaxSuggRes, IMSSOFFLIN23_n210DFDomMaxSuggRes, IMSSOFFLIN23_A209DFDomForceSuggSel, IMSSOFFLIN23_n209DFDomForceSuggSel, IMSSOFFLIN23_A208DFDomMinCntCharSugg, IMSSOFFLIN23_n208DFDomMinCntCharSugg, IMSSOFFLIN23_A211DFDomDftVal, IMSSOFFLIN23_n211DFDomDftVal, IMSSOFFLIN23_A219DFDomCntCols,
            IMSSOFFLIN23_A218DFDomCntRows, IMSSOFFLIN23_A217DFDomCntDec, IMSSOFFLIN23_A223DFDomWth, IMSSOFFLIN23_A207DFDomLen, IMSSOFFLIN23_A198DFDomDsp, IMSSOFFLIN23_n198DFDomDsp, IMSSOFFLIN23_A197DFDomType, IMSSOFFLIN23_A227DFDomGUID, IMSSOFFLIN23_A206DFDomDsc, IMSSOFFLIN23_A111DFDomId
            }
            , new Object[] {
            IMSSOFFLIN24_A117DFSubElemFormPos, IMSSOFFLIN24_n117DFSubElemFormPos, IMSSOFFLIN24_A109DFSubElemFormElemVer, IMSSOFFLIN24_A108DFSubElemFormElemId, IMSSOFFLIN24_A89DFElemVer, IMSSOFFLIN24_A88DFElemId, IMSSOFFLIN24_A87DFFormVer, IMSSOFFLIN24_A86DFFormId
            }
            , new Object[] {
            IMSSOFFLIN25_A120DFFilElemFormElemVer, IMSSOFFLIN25_A119DFFilElemFormElemId, IMSSOFFLIN25_A121DFFilElemFormPos, IMSSOFFLIN25_A118DFFilElemFormId, IMSSOFFLIN25_A89DFElemVer, IMSSOFFLIN25_A88DFElemId, IMSSOFFLIN25_A87DFFormVer, IMSSOFFLIN25_A86DFFormId
            }
            , new Object[] {
            IMSSOFFLIN26_A288HospitalId, IMSSOFFLIN26_n288HospitalId, IMSSOFFLIN26_A36ServicioDescripcion, IMSSOFFLIN26_A6ServicioId
            }
            , new Object[] {
            IMSSOFFLIN27_A105DFFormInstFormId, IMSSOFFLIN27_A141DFUplFileExt, IMSSOFFLIN27_A142DFUplFileName, IMSSOFFLIN27_A140DFUplFile, IMSSOFFLIN27_A91DFUplKey, IMSSOFFLIN27_A90DFFormInstId
            }
         }
      );
      /* GeneXus formulas. */
      Gx_err = (short)(0) ;
   }

   protected short gxsyncstatus ;
   protected short gxischeck ;
   protected short gxstatus ;
   protected short gxerrorstatus ;
   protected short A6ServicioId ;
   protected short A323nada ;
   protected short A309TextoId ;
   protected short A5DXAuxImagenId ;
   protected short A4DXAuxDoctoId ;
   protected short A321PacienteServicioId ;
   protected short A50PacienteEdad ;
   protected short A305ExtensionTipo ;
   protected short A304ExtensionId ;
   protected short A121DFFilElemFormPos ;
   protected short A288HospitalId ;
   protected short GXv_int8[] ;
   protected short Gx_err ;
   protected int A1CIE10Id ;
   protected int A102DFParmId ;
   protected int A291PacienteCie10Id ;
   protected int A235DFFormPmtHgh ;
   protected int A234DFFormPmtWth ;
   protected int A87DFFormVer ;
   protected int A86DFFormId ;
   protected int A284DFElemFormPrtNumColSkip ;
   protected int A276DFElemFormPrtNumRowSkip ;
   protected int A116DFElemFormPos ;
   protected int A89DFElemVer ;
   protected int A88DFElemId ;
   protected int A108DFSubElemFormElemId ;
   protected int A109DFSubElemFormElemVer ;
   protected int A110DFElemFormInstSubElemRow ;
   protected int A107DFElemFormInstSubElemId ;
   protected int A113DFDomStaValOptOrd ;
   protected int A111DFDomId ;
   protected int A106DFFormInstFormVer ;
   protected int A105DFFormInstFormId ;
   protected int A282DFElemPrtNumColSkip ;
   protected int A277DFElemPrtNumRowSkip ;
   protected int A251DFElemMaxSuggRes ;
   protected int A249DFElemMinCntCharSugg ;
   protected int A244DFElemCntCols ;
   protected int A243DFElemCntRows ;
   protected int A242DFElemCntDec ;
   protected int A258DFElemWth ;
   protected int A239DFElemLen ;
   protected int A92DFFormRstId ;
   protected int A100DFUserRstId ;
   protected int A210DFDomMaxSuggRes ;
   protected int A208DFDomMinCntCharSugg ;
   protected int A219DFDomCntCols ;
   protected int A218DFDomCntRows ;
   protected int A217DFDomCntDec ;
   protected int A223DFDomWth ;
   protected int A207DFDomLen ;
   protected int A117DFSubElemFormPos ;
   protected int A120DFFilElemFormElemVer ;
   protected int A119DFFilElemFormElemId ;
   protected int A118DFFilElemFormId ;
   protected long A297MedicoMatricula ;
   protected long GXV1 ;
   protected long A34MMatricula ;
   protected long A30MBMatricula ;
   protected long A26JSMatricula ;
   protected long A90DFFormInstId ;
   protected long A84FormatoPacienteMedicoMatricula ;
   protected String AV4Matricula ;
   protected String AV5UserMedico ;
   protected String GXt_char1 ;
   protected String GXv_char2[] ;
   protected String scmdbuf ;
   protected String A296MedicoApellidoMaterno ;
   protected String A295MedicoApellidoPaterno ;
   protected String A294MedicoSegundoNombre ;
   protected String A293MedicoPrimerNombre ;
   protected String A292UserMedico ;
   protected String gxlinehash ;
   protected String gxtabledata ;
   protected String gxtablecurrenthash ;
   protected String gxtablestoredhash ;
   protected String gxdeviceidentifier ;
   protected String A81Matricula ;
   protected String A3PacienteAgregado ;
   protected String A2PacienteNSS ;
   protected String A33MApMat ;
   protected String A32MApPat ;
   protected String A29MBApMat ;
   protected String A28MBApPat ;
   protected String A27MBNombre ;
   protected String A25JSApMat ;
   protected String A24JSApPat ;
   protected String A23JSNombre ;
   protected String A20Cama ;
   protected String A168DFParmVal ;
   protected String A167DFParmName ;
   protected String A322DXAuxImagenExtension ;
   protected String A73DXAuxImagenNombre ;
   protected String A16DXAuxImagenUserAlta ;
   protected String A74DXAuxDoctoNombre ;
   protected String A82DXAuxDoctoExtension ;
   protected String A13DXAuxDoctoUserAlta ;
   protected String A72PacienteCama ;
   protected String A55PacienteNombreCompleto ;
   protected String A54PacienteReferencia ;
   protected String A52PacienteTelefono ;
   protected String A51PacienteGenero ;
   protected String A46PacienteApMat ;
   protected String A45PacienteApPat ;
   protected String A44PacienteNombre ;
   protected String A171DFFormName ;
   protected String A80FormatoPacienteAgregado ;
   protected String A79FormatoPacienteNSS ;
   protected String A306ExtensionNombre ;
   protected String A187DFElemFormIsFlt ;
   protected String A186DFElemFormCmpWth ;
   protected String A185DFElemFormLblWth ;
   protected String A273DFElemFormPrtName ;
   protected String A184DFElemFormInhType ;
   protected String A188DFElemFormName ;
   protected String A147DFElemFormInstFileName ;
   protected String A146DFElemFormInstFileType ;
   protected String A150DFElemFormInstSubElemFileName ;
   protected String A149DFElemFormInstSubElemFileType ;
   protected String A290DFTempFm ;
   protected String A287DFTempOutFm ;
   protected String A136DFTempName ;
   protected String A225DFDomStaValOptDsc ;
   protected String A112DFDomStaValOptCod ;
   protected String A272DFElemPrtName ;
   protected String A260DFElemLblWth ;
   protected String A246DFElemCmpWth ;
   protected String A245DFElemIsFlt ;
   protected String A259DFElemFileType ;
   protected String A257DFElemRegexVal ;
   protected String A270DFElemBtnPos ;
   protected String A271DFElemShwNbrLbl ;
   protected String A183DFElemDftVal ;
   protected String A199DFElemDsp ;
   protected String A181DFElemType ;
   protected String A195DFElemClsName ;
   protected String A151DFElemName ;
   protected String A93DFFormRstVal ;
   protected String A101DFUserRstVal ;
   protected String A226DFDomLblWth ;
   protected String A222DFDomCmpWth ;
   protected String A221DFDomIsFlt ;
   protected String A224DFDomFileType ;
   protected String A220DFDomRegexVal ;
   protected String A211DFDomDftVal ;
   protected String A198DFDomDsp ;
   protected String A197DFDomType ;
   protected String A206DFDomDsc ;
   protected String A36ServicioDescripcion ;
   protected String A141DFUplFileExt ;
   protected String A142DFUplFileName ;
   protected String A91DFUplKey ;
   protected String gxsourcever ;
   protected String DEVICEID ;
   protected String QUERYID ;
   protected String RESULTSET ;
   protected java.util.Date A300MedicoUltimaActualizacion ;
   protected java.util.Date A22DiagnosticoCirugiaFecha ;
   protected java.util.Date A35DiagnosticoFechaAlta ;
   protected java.util.Date A15DXAuxImagenFechaAlta ;
   protected java.util.Date A12DXAuxDoctoFechaAlta ;
   protected java.util.Date A157DFFormInstDT ;
   protected java.util.Date A17DiagnosticoFechaIngreso ;
   protected java.util.Date A76PAcienteFechaIngreso ;
   protected java.util.Date A68PacienteFechaNacimiento ;
   protected boolean returnInSub ;
   protected boolean A312MedicoDebeMostarTerm ;
   protected boolean A302MedicoDebeValidarDatos ;
   protected boolean n297MedicoMatricula ;
   protected boolean n34MMatricula ;
   protected boolean n33MApMat ;
   protected boolean n32MApPat ;
   protected boolean n31MNombre ;
   protected boolean n30MBMatricula ;
   protected boolean n29MBApMat ;
   protected boolean n28MBApPat ;
   protected boolean n27MBNombre ;
   protected boolean n26JSMatricula ;
   protected boolean n25JSApMat ;
   protected boolean n24JSApPat ;
   protected boolean n23JSNombre ;
   protected boolean n22DiagnosticoCirugiaFecha ;
   protected boolean n21DiagnosticoCirugia ;
   protected boolean n20Cama ;
   protected boolean n19DiagnosticoResumen ;
   protected boolean n18DiagnosticoComplemento ;
   protected boolean n35DiagnosticoFechaAlta ;
   protected boolean n17DiagnosticoFechaIngreso ;
   protected boolean A169DFParmIsMetaData ;
   protected boolean n54PacienteReferencia ;
   protected boolean n53PacienteFamiliar ;
   protected boolean n52PacienteTelefono ;
   protected boolean n51PacienteGenero ;
   protected boolean n46PacienteApMat ;
   protected boolean A303DFFormIsSD ;
   protected boolean A159DFFormRunDLT ;
   protected boolean n235DFFormPmtHgh ;
   protected boolean n234DFFormPmtWth ;
   protected boolean A237DFFormAct ;
   protected boolean A313DFElemFormReq ;
   protected boolean n307DFElemFormLoadRule ;
   protected boolean n266DFElemFormMetadata ;
   protected boolean A267DFElemFormShwNbr ;
   protected boolean n267DFElemFormShwNbr ;
   protected boolean A265DFElemFormDateSel ;
   protected boolean n265DFElemFormDateSel ;
   protected boolean A262DFElemFormHasPmpt ;
   protected boolean n262DFElemFormHasPmpt ;
   protected boolean n187DFElemFormIsFlt ;
   protected boolean n186DFElemFormCmpWth ;
   protected boolean n185DFElemFormLblWth ;
   protected boolean A285DFElemFormPrtShwNbr ;
   protected boolean A274DFElemFormPrtAddRows ;
   protected boolean A194DFElemFormIsVisPrt ;
   protected boolean A193DFElemFormIsVis ;
   protected boolean A192DFElemFormIsColap ;
   protected boolean A191DFElemFormAllowIns ;
   protected boolean n191DFElemFormAllowIns ;
   protected boolean A190DFElemFormAllowUpd ;
   protected boolean n190DFElemFormAllowUpd ;
   protected boolean A189DFElemFormAllowDlt ;
   protected boolean n189DFElemFormAllowDlt ;
   protected boolean n147DFElemFormInstFileName ;
   protected boolean n146DFElemFormInstFileType ;
   protected boolean n145DFElemFormInstBlob ;
   protected boolean n143DFElemFormInstVal ;
   protected boolean n150DFElemFormInstSubElemFileName ;
   protected boolean n149DFElemFormInstSubElemFileType ;
   protected boolean n144DFElemFormInstSubElemVal ;
   protected boolean n148DFElemFormInstSubElemBlob ;
   protected boolean n111DFDomId ;
   protected boolean n200DFFormInstSignedPDF ;
   protected boolean n201DFFormInstSignedBy ;
   protected boolean A314DFElemReq ;
   protected boolean n308DFElemLoadRule ;
   protected boolean n268DFElemMetadata ;
   protected boolean A241DFElemIsColap ;
   protected boolean A283DFElemPrtShwNbr ;
   protected boolean A275DFElemPrtAddRows ;
   protected boolean A263DFElemIsVisPrt ;
   protected boolean A240DFElemIsVis ;
   protected boolean n260DFElemLblWth ;
   protected boolean n246DFElemCmpWth ;
   protected boolean n245DFElemIsFlt ;
   protected boolean n259DFElemFileType ;
   protected boolean n257DFElemRegexVal ;
   protected boolean A256DFElemAllowDlt ;
   protected boolean n256DFElemAllowDlt ;
   protected boolean A255DFElemAllowUpd ;
   protected boolean n255DFElemAllowUpd ;
   protected boolean A254DFElemAllowIns ;
   protected boolean n254DFElemAllowIns ;
   protected boolean A253DFElemUseBtns ;
   protected boolean n253DFElemUseBtns ;
   protected boolean A252DFElemIsOrd ;
   protected boolean n252DFElemIsOrd ;
   protected boolean n251DFElemMaxSuggRes ;
   protected boolean A250DFElemForceSuggSel ;
   protected boolean n250DFElemForceSuggSel ;
   protected boolean n249DFElemMinCntCharSugg ;
   protected boolean n248DFElemLoadPrgName ;
   protected boolean n270DFElemBtnPos ;
   protected boolean n271DFElemShwNbrLbl ;
   protected boolean A269DFElemShwNbr ;
   protected boolean n269DFElemShwNbr ;
   protected boolean A264DFElemDateSel ;
   protected boolean n264DFElemDateSel ;
   protected boolean A247DFElemHasPmpt ;
   protected boolean n247DFElemHasPmpt ;
   protected boolean n183DFElemDftVal ;
   protected boolean n244DFElemCntCols ;
   protected boolean n243DFElemCntRows ;
   protected boolean n242DFElemCntDec ;
   protected boolean n258DFElemWth ;
   protected boolean n239DFElemLen ;
   protected boolean n199DFElemDsp ;
   protected boolean n195DFElemClsName ;
   protected boolean n238DFElemDsc ;
   protected boolean A166DFUserRstPwdIni ;
   protected boolean A319DFDomPrtDsc ;
   protected boolean n319DFDomPrtDsc ;
   protected boolean n226DFDomLblWth ;
   protected boolean n222DFDomCmpWth ;
   protected boolean n221DFDomIsFlt ;
   protected boolean n224DFDomFileType ;
   protected boolean A216DFDomAllowDlt ;
   protected boolean n216DFDomAllowDlt ;
   protected boolean A215DFDomAllowUpd ;
   protected boolean n215DFDomAllowUpd ;
   protected boolean A214DFDomAllowIns ;
   protected boolean n214DFDomAllowIns ;
   protected boolean A213DFDomUseBtns ;
   protected boolean n213DFDomUseBtns ;
   protected boolean A212DFDomIsOrd ;
   protected boolean n212DFDomIsOrd ;
   protected boolean n210DFDomMaxSuggRes ;
   protected boolean A209DFDomForceSuggSel ;
   protected boolean n209DFDomForceSuggSel ;
   protected boolean n208DFDomMinCntCharSugg ;
   protected boolean n211DFDomDftVal ;
   protected boolean n198DFDomDsp ;
   protected boolean n117DFSubElemFormPos ;
   protected boolean n288HospitalId ;
   protected String A21DiagnosticoCirugia ;
   protected String A19DiagnosticoResumen ;
   protected String A18DiagnosticoComplemento ;
   protected String A311TextoDescripcion ;
   protected String A11DXAuxDoctoDocumento ;
   protected String A145DFElemFormInstBlob ;
   protected String A148DFElemFormInstSubElemBlob ;
   protected String A280DFTempBlob ;
   protected String A200DFFormInstSignedPDF ;
   protected String A140DFUplFile ;
   protected String A75PacienteNSSAgregado ;
   protected String A69CIECodigo ;
   protected String A10CIE10Descripcion ;
   protected String A31MNombre ;
   protected String A310TextoTitulo ;
   protected String A40000DXAuxImagenImg_GXI ;
   protected String A298PacienteDiagnosticoPhone ;
   protected String A71PacienteDiagnosticoResumido ;
   protected String A70PacienteDiagnostico ;
   protected String A53PacienteFamiliar ;
   protected String A317DFFormDsc ;
   protected String A236DFFormHelpURL ;
   protected String A176DFFormPrefix ;
   protected String A85FormatoPacienteMedicoNombre ;
   protected String A316DFElemFormPrtPic ;
   protected String A307DFElemFormLoadRule ;
   protected String A266DFElemFormMetadata ;
   protected String A143DFElemFormInstVal ;
   protected String A144DFElemFormInstSubElemVal ;
   protected String A281DFTempAddParmPrgName ;
   protected String A286DFTempDsc ;
   protected String A201DFFormInstSignedBy ;
   protected String A315DFElemPrtPic ;
   protected String A308DFElemLoadRule ;
   protected String A268DFElemMetadata ;
   protected String A261DFElemDscPrgName ;
   protected String A248DFElemLoadPrgName ;
   protected String A238DFElemDsc ;
   protected String A99DFUserExtId ;
   protected String A14DXAuxImagenImg ;
   protected java.util.UUID A115DFFormGuid ;
   protected java.util.UUID A114DFElemGuid ;
   protected java.util.UUID A227DFDomGUID ;
   protected com.genexus.internet.HttpRequest gxhttpr ;
   protected com.genexus.internet.StringCollection gxsyncheader ;
   protected com.genexus.internet.StringCollection gxsyncline ;
   protected com.genexus.internet.StringCollection gxsyncline_hash ;
   protected com.genexus.internet.StringCollection gxtablemdata ;
   protected com.genexus.internet.StringCollection gxsynchashkey ;
   protected com.genexus.internet.StringCollection gxsetline ;
   protected com.genexus.internet.StringCollection gxsyncheaderpre ;
   protected com.genexus.internet.StringCollection gxsyncheaderline ;
   protected com.genexus.GxUnknownObjectCollection gxsyncresponse ;
   protected com.genexus.GxUnknownObjectCollection gxsyncresponse_hash ;
   protected com.genexus.GxUnknownObjectCollection gxfinalsync ;
   protected com.genexus.GxUnknownObjectCollection gxsynchashset ;
   protected com.genexus.GxUnknownObjectCollection gxsyncvalueset ;
   protected com.genexus.GxUnknownObjectCollection gxsetvalueline ;
   protected com.genexus.GxUnknownObjectCollection gxsyncinsert ;
   protected com.genexus.GxUnknownObjectCollection gxsyncupdate ;
   protected com.genexus.GxUnknownObjectCollection gxsyncdelete ;
   protected com.genexus.GxUnknownObjectCollection gxtablehashlist ;
   protected com.genexus.GxUnknownObjectCollection GXv_objcol_gxjsonable7[] ;
   protected com.genexus.GxUnknownObjectCollection GXv_objcol_gxjsonable6[] ;
   protected com.genexus.GxUnknownObjectCollection GXv_objcol_gxjsonable5[] ;
   protected com.genexus.GxUnknownObjectCollection gxallsyncresponse ;
   protected com.genexus.GxUnknownObjectCollection gxtableheadlist ;
   protected IDataStoreProvider pr_default ;
   protected boolean[] IMSSOFFLIN2_A312MedicoDebeMostarTerm ;
   protected boolean[] IMSSOFFLIN2_A302MedicoDebeValidarDatos ;
   protected java.util.Date[] IMSSOFFLIN2_A300MedicoUltimaActualizacion ;
   protected long[] IMSSOFFLIN2_A297MedicoMatricula ;
   protected boolean[] IMSSOFFLIN2_n297MedicoMatricula ;
   protected String[] IMSSOFFLIN2_A296MedicoApellidoMaterno ;
   protected String[] IMSSOFFLIN2_A295MedicoApellidoPaterno ;
   protected String[] IMSSOFFLIN2_A294MedicoSegundoNombre ;
   protected String[] IMSSOFFLIN2_A293MedicoPrimerNombre ;
   protected String[] IMSSOFFLIN2_A292UserMedico ;
   protected String[] IMSSOFFLIN3_A75PacienteNSSAgregado ;
   protected String[] IMSSOFFLIN3_A81Matricula ;
   protected String[] IMSSOFFLIN3_A3PacienteAgregado ;
   protected String[] IMSSOFFLIN3_A2PacienteNSS ;
   protected String[] IMSSOFFLIN4_A69CIECodigo ;
   protected String[] IMSSOFFLIN4_A10CIE10Descripcion ;
   protected int[] IMSSOFFLIN4_A1CIE10Id ;
   protected String[] IMSSOFFLIN5_A75PacienteNSSAgregado ;
   protected long[] IMSSOFFLIN5_A34MMatricula ;
   protected boolean[] IMSSOFFLIN5_n34MMatricula ;
   protected String[] IMSSOFFLIN5_A33MApMat ;
   protected boolean[] IMSSOFFLIN5_n33MApMat ;
   protected String[] IMSSOFFLIN5_A32MApPat ;
   protected boolean[] IMSSOFFLIN5_n32MApPat ;
   protected String[] IMSSOFFLIN5_A31MNombre ;
   protected boolean[] IMSSOFFLIN5_n31MNombre ;
   protected long[] IMSSOFFLIN5_A30MBMatricula ;
   protected boolean[] IMSSOFFLIN5_n30MBMatricula ;
   protected String[] IMSSOFFLIN5_A29MBApMat ;
   protected boolean[] IMSSOFFLIN5_n29MBApMat ;
   protected String[] IMSSOFFLIN5_A28MBApPat ;
   protected boolean[] IMSSOFFLIN5_n28MBApPat ;
   protected String[] IMSSOFFLIN5_A27MBNombre ;
   protected boolean[] IMSSOFFLIN5_n27MBNombre ;
   protected long[] IMSSOFFLIN5_A26JSMatricula ;
   protected boolean[] IMSSOFFLIN5_n26JSMatricula ;
   protected String[] IMSSOFFLIN5_A25JSApMat ;
   protected boolean[] IMSSOFFLIN5_n25JSApMat ;
   protected String[] IMSSOFFLIN5_A24JSApPat ;
   protected boolean[] IMSSOFFLIN5_n24JSApPat ;
   protected String[] IMSSOFFLIN5_A23JSNombre ;
   protected boolean[] IMSSOFFLIN5_n23JSNombre ;
   protected java.util.Date[] IMSSOFFLIN5_A22DiagnosticoCirugiaFecha ;
   protected boolean[] IMSSOFFLIN5_n22DiagnosticoCirugiaFecha ;
   protected String[] IMSSOFFLIN5_A21DiagnosticoCirugia ;
   protected boolean[] IMSSOFFLIN5_n21DiagnosticoCirugia ;
   protected String[] IMSSOFFLIN5_A20Cama ;
   protected boolean[] IMSSOFFLIN5_n20Cama ;
   protected short[] IMSSOFFLIN5_A6ServicioId ;
   protected String[] IMSSOFFLIN5_A19DiagnosticoResumen ;
   protected boolean[] IMSSOFFLIN5_n19DiagnosticoResumen ;
   protected String[] IMSSOFFLIN5_A18DiagnosticoComplemento ;
   protected boolean[] IMSSOFFLIN5_n18DiagnosticoComplemento ;
   protected java.util.Date[] IMSSOFFLIN5_A35DiagnosticoFechaAlta ;
   protected boolean[] IMSSOFFLIN5_n35DiagnosticoFechaAlta ;
   protected java.util.Date[] IMSSOFFLIN5_A17DiagnosticoFechaIngreso ;
   protected boolean[] IMSSOFFLIN5_n17DiagnosticoFechaIngreso ;
   protected int[] IMSSOFFLIN5_A1CIE10Id ;
   protected String[] IMSSOFFLIN5_A3PacienteAgregado ;
   protected String[] IMSSOFFLIN5_A2PacienteNSS ;
   protected short[] IMSSOFFLIN6_A323nada ;
   protected String[] IMSSOFFLIN6_A311TextoDescripcion ;
   protected String[] IMSSOFFLIN6_A310TextoTitulo ;
   protected short[] IMSSOFFLIN6_A309TextoId ;
   protected boolean[] IMSSOFFLIN7_A169DFParmIsMetaData ;
   protected String[] IMSSOFFLIN7_A168DFParmVal ;
   protected String[] IMSSOFFLIN7_A167DFParmName ;
   protected int[] IMSSOFFLIN7_A102DFParmId ;
   protected String[] IMSSOFFLIN8_A75PacienteNSSAgregado ;
   protected String[] IMSSOFFLIN8_A40000DXAuxImagenImg_GXI ;
   protected String[] IMSSOFFLIN8_A322DXAuxImagenExtension ;
   protected String[] IMSSOFFLIN8_A73DXAuxImagenNombre ;
   protected String[] IMSSOFFLIN8_A16DXAuxImagenUserAlta ;
   protected java.util.Date[] IMSSOFFLIN8_A15DXAuxImagenFechaAlta ;
   protected String[] IMSSOFFLIN8_A14DXAuxImagenImg ;
   protected short[] IMSSOFFLIN8_A5DXAuxImagenId ;
   protected int[] IMSSOFFLIN8_A1CIE10Id ;
   protected String[] IMSSOFFLIN8_A3PacienteAgregado ;
   protected String[] IMSSOFFLIN8_A2PacienteNSS ;
   protected String[] IMSSOFFLIN9_A75PacienteNSSAgregado ;
   protected String[] IMSSOFFLIN9_A74DXAuxDoctoNombre ;
   protected String[] IMSSOFFLIN9_A82DXAuxDoctoExtension ;
   protected String[] IMSSOFFLIN9_A13DXAuxDoctoUserAlta ;
   protected java.util.Date[] IMSSOFFLIN9_A12DXAuxDoctoFechaAlta ;
   protected String[] IMSSOFFLIN9_A11DXAuxDoctoDocumento ;
   protected short[] IMSSOFFLIN9_A4DXAuxDoctoId ;
   protected int[] IMSSOFFLIN9_A1CIE10Id ;
   protected String[] IMSSOFFLIN9_A3PacienteAgregado ;
   protected String[] IMSSOFFLIN9_A2PacienteNSS ;
   protected short[] IMSSOFFLIN10_A321PacienteServicioId ;
   protected String[] IMSSOFFLIN10_A298PacienteDiagnosticoPhone ;
   protected int[] IMSSOFFLIN10_A291PacienteCie10Id ;
   protected java.util.Date[] IMSSOFFLIN10_A76PAcienteFechaIngreso ;
   protected String[] IMSSOFFLIN10_A75PacienteNSSAgregado ;
   protected String[] IMSSOFFLIN10_A72PacienteCama ;
   protected String[] IMSSOFFLIN10_A71PacienteDiagnosticoResumido ;
   protected String[] IMSSOFFLIN10_A70PacienteDiagnostico ;
   protected java.util.Date[] IMSSOFFLIN10_A68PacienteFechaNacimiento ;
   protected String[] IMSSOFFLIN10_A55PacienteNombreCompleto ;
   protected String[] IMSSOFFLIN10_A54PacienteReferencia ;
   protected boolean[] IMSSOFFLIN10_n54PacienteReferencia ;
   protected String[] IMSSOFFLIN10_A53PacienteFamiliar ;
   protected boolean[] IMSSOFFLIN10_n53PacienteFamiliar ;
   protected String[] IMSSOFFLIN10_A52PacienteTelefono ;
   protected boolean[] IMSSOFFLIN10_n52PacienteTelefono ;
   protected String[] IMSSOFFLIN10_A51PacienteGenero ;
   protected boolean[] IMSSOFFLIN10_n51PacienteGenero ;
   protected short[] IMSSOFFLIN10_A50PacienteEdad ;
   protected String[] IMSSOFFLIN10_A46PacienteApMat ;
   protected boolean[] IMSSOFFLIN10_n46PacienteApMat ;
   protected String[] IMSSOFFLIN10_A45PacienteApPat ;
   protected String[] IMSSOFFLIN10_A44PacienteNombre ;
   protected String[] IMSSOFFLIN10_A3PacienteAgregado ;
   protected String[] IMSSOFFLIN10_A2PacienteNSS ;
   protected String[] IMSSOFFLIN11_A317DFFormDsc ;
   protected boolean[] IMSSOFFLIN11_A303DFFormIsSD ;
   protected boolean[] IMSSOFFLIN11_A159DFFormRunDLT ;
   protected String[] IMSSOFFLIN11_A236DFFormHelpURL ;
   protected String[] IMSSOFFLIN11_A176DFFormPrefix ;
   protected int[] IMSSOFFLIN11_A235DFFormPmtHgh ;
   protected boolean[] IMSSOFFLIN11_n235DFFormPmtHgh ;
   protected int[] IMSSOFFLIN11_A234DFFormPmtWth ;
   protected boolean[] IMSSOFFLIN11_n234DFFormPmtWth ;
   protected boolean[] IMSSOFFLIN11_A237DFFormAct ;
   protected String[] IMSSOFFLIN11_A171DFFormName ;
   protected java.util.UUID[] IMSSOFFLIN11_A115DFFormGuid ;
   protected int[] IMSSOFFLIN11_A87DFFormVer ;
   protected int[] IMSSOFFLIN11_A86DFFormId ;
   protected String[] IMSSOFFLIN12_A85FormatoPacienteMedicoNombre ;
   protected long[] IMSSOFFLIN12_A84FormatoPacienteMedicoMatricula ;
   protected long[] IMSSOFFLIN12_A90DFFormInstId ;
   protected String[] IMSSOFFLIN12_A80FormatoPacienteAgregado ;
   protected String[] IMSSOFFLIN12_A79FormatoPacienteNSS ;
   protected String[] IMSSOFFLIN13_A306ExtensionNombre ;
   protected short[] IMSSOFFLIN13_A305ExtensionTipo ;
   protected short[] IMSSOFFLIN13_A304ExtensionId ;
   protected boolean[] IMSSOFFLIN14_A313DFElemFormReq ;
   protected String[] IMSSOFFLIN14_A316DFElemFormPrtPic ;
   protected String[] IMSSOFFLIN14_A307DFElemFormLoadRule ;
   protected boolean[] IMSSOFFLIN14_n307DFElemFormLoadRule ;
   protected String[] IMSSOFFLIN14_A266DFElemFormMetadata ;
   protected boolean[] IMSSOFFLIN14_n266DFElemFormMetadata ;
   protected boolean[] IMSSOFFLIN14_A267DFElemFormShwNbr ;
   protected boolean[] IMSSOFFLIN14_n267DFElemFormShwNbr ;
   protected boolean[] IMSSOFFLIN14_A265DFElemFormDateSel ;
   protected boolean[] IMSSOFFLIN14_n265DFElemFormDateSel ;
   protected boolean[] IMSSOFFLIN14_A262DFElemFormHasPmpt ;
   protected boolean[] IMSSOFFLIN14_n262DFElemFormHasPmpt ;
   protected String[] IMSSOFFLIN14_A187DFElemFormIsFlt ;
   protected boolean[] IMSSOFFLIN14_n187DFElemFormIsFlt ;
   protected String[] IMSSOFFLIN14_A186DFElemFormCmpWth ;
   protected boolean[] IMSSOFFLIN14_n186DFElemFormCmpWth ;
   protected String[] IMSSOFFLIN14_A185DFElemFormLblWth ;
   protected boolean[] IMSSOFFLIN14_n185DFElemFormLblWth ;
   protected boolean[] IMSSOFFLIN14_A285DFElemFormPrtShwNbr ;
   protected int[] IMSSOFFLIN14_A284DFElemFormPrtNumColSkip ;
   protected int[] IMSSOFFLIN14_A276DFElemFormPrtNumRowSkip ;
   protected boolean[] IMSSOFFLIN14_A274DFElemFormPrtAddRows ;
   protected String[] IMSSOFFLIN14_A273DFElemFormPrtName ;
   protected boolean[] IMSSOFFLIN14_A194DFElemFormIsVisPrt ;
   protected boolean[] IMSSOFFLIN14_A193DFElemFormIsVis ;
   protected boolean[] IMSSOFFLIN14_A192DFElemFormIsColap ;
   protected boolean[] IMSSOFFLIN14_A191DFElemFormAllowIns ;
   protected boolean[] IMSSOFFLIN14_n191DFElemFormAllowIns ;
   protected boolean[] IMSSOFFLIN14_A190DFElemFormAllowUpd ;
   protected boolean[] IMSSOFFLIN14_n190DFElemFormAllowUpd ;
   protected boolean[] IMSSOFFLIN14_A189DFElemFormAllowDlt ;
   protected boolean[] IMSSOFFLIN14_n189DFElemFormAllowDlt ;
   protected String[] IMSSOFFLIN14_A184DFElemFormInhType ;
   protected int[] IMSSOFFLIN14_A116DFElemFormPos ;
   protected String[] IMSSOFFLIN14_A188DFElemFormName ;
   protected int[] IMSSOFFLIN14_A89DFElemVer ;
   protected int[] IMSSOFFLIN14_A88DFElemId ;
   protected int[] IMSSOFFLIN14_A87DFFormVer ;
   protected int[] IMSSOFFLIN14_A86DFFormId ;
   protected String[] IMSSOFFLIN15_A147DFElemFormInstFileName ;
   protected boolean[] IMSSOFFLIN15_n147DFElemFormInstFileName ;
   protected String[] IMSSOFFLIN15_A146DFElemFormInstFileType ;
   protected boolean[] IMSSOFFLIN15_n146DFElemFormInstFileType ;
   protected String[] IMSSOFFLIN15_A145DFElemFormInstBlob ;
   protected boolean[] IMSSOFFLIN15_n145DFElemFormInstBlob ;
   protected String[] IMSSOFFLIN15_A143DFElemFormInstVal ;
   protected boolean[] IMSSOFFLIN15_n143DFElemFormInstVal ;
   protected int[] IMSSOFFLIN15_A89DFElemVer ;
   protected int[] IMSSOFFLIN15_A88DFElemId ;
   protected long[] IMSSOFFLIN15_A90DFFormInstId ;
   protected String[] IMSSOFFLIN16_A150DFElemFormInstSubElemFileName ;
   protected boolean[] IMSSOFFLIN16_n150DFElemFormInstSubElemFileName ;
   protected String[] IMSSOFFLIN16_A149DFElemFormInstSubElemFileType ;
   protected boolean[] IMSSOFFLIN16_n149DFElemFormInstSubElemFileType ;
   protected int[] IMSSOFFLIN16_A108DFSubElemFormElemId ;
   protected int[] IMSSOFFLIN16_A109DFSubElemFormElemVer ;
   protected int[] IMSSOFFLIN16_A110DFElemFormInstSubElemRow ;
   protected String[] IMSSOFFLIN16_A144DFElemFormInstSubElemVal ;
   protected boolean[] IMSSOFFLIN16_n144DFElemFormInstSubElemVal ;
   protected String[] IMSSOFFLIN16_A148DFElemFormInstSubElemBlob ;
   protected boolean[] IMSSOFFLIN16_n148DFElemFormInstSubElemBlob ;
   protected int[] IMSSOFFLIN16_A107DFElemFormInstSubElemId ;
   protected int[] IMSSOFFLIN16_A89DFElemVer ;
   protected int[] IMSSOFFLIN16_A88DFElemId ;
   protected long[] IMSSOFFLIN16_A90DFFormInstId ;
   protected String[] IMSSOFFLIN17_A290DFTempFm ;
   protected String[] IMSSOFFLIN17_A287DFTempOutFm ;
   protected String[] IMSSOFFLIN17_A281DFTempAddParmPrgName ;
   protected String[] IMSSOFFLIN17_A280DFTempBlob ;
   protected String[] IMSSOFFLIN17_A286DFTempDsc ;
   protected String[] IMSSOFFLIN17_A136DFTempName ;
   protected int[] IMSSOFFLIN17_A87DFFormVer ;
   protected int[] IMSSOFFLIN17_A86DFFormId ;
   protected String[] IMSSOFFLIN18_A225DFDomStaValOptDsc ;
   protected int[] IMSSOFFLIN18_A113DFDomStaValOptOrd ;
   protected String[] IMSSOFFLIN18_A112DFDomStaValOptCod ;
   protected int[] IMSSOFFLIN18_A111DFDomId ;
   protected boolean[] IMSSOFFLIN18_n111DFDomId ;
   protected String[] IMSSOFFLIN19_A200DFFormInstSignedPDF ;
   protected boolean[] IMSSOFFLIN19_n200DFFormInstSignedPDF ;
   protected String[] IMSSOFFLIN19_A201DFFormInstSignedBy ;
   protected boolean[] IMSSOFFLIN19_n201DFFormInstSignedBy ;
   protected java.util.Date[] IMSSOFFLIN19_A157DFFormInstDT ;
   protected int[] IMSSOFFLIN19_A106DFFormInstFormVer ;
   protected int[] IMSSOFFLIN19_A105DFFormInstFormId ;
   protected long[] IMSSOFFLIN19_A90DFFormInstId ;
   protected boolean[] IMSSOFFLIN20_A314DFElemReq ;
   protected String[] IMSSOFFLIN20_A315DFElemPrtPic ;
   protected String[] IMSSOFFLIN20_A308DFElemLoadRule ;
   protected boolean[] IMSSOFFLIN20_n308DFElemLoadRule ;
   protected String[] IMSSOFFLIN20_A268DFElemMetadata ;
   protected boolean[] IMSSOFFLIN20_n268DFElemMetadata ;
   protected boolean[] IMSSOFFLIN20_A241DFElemIsColap ;
   protected boolean[] IMSSOFFLIN20_A283DFElemPrtShwNbr ;
   protected int[] IMSSOFFLIN20_A282DFElemPrtNumColSkip ;
   protected int[] IMSSOFFLIN20_A277DFElemPrtNumRowSkip ;
   protected boolean[] IMSSOFFLIN20_A275DFElemPrtAddRows ;
   protected String[] IMSSOFFLIN20_A272DFElemPrtName ;
   protected boolean[] IMSSOFFLIN20_A263DFElemIsVisPrt ;
   protected boolean[] IMSSOFFLIN20_A240DFElemIsVis ;
   protected String[] IMSSOFFLIN20_A260DFElemLblWth ;
   protected boolean[] IMSSOFFLIN20_n260DFElemLblWth ;
   protected String[] IMSSOFFLIN20_A246DFElemCmpWth ;
   protected boolean[] IMSSOFFLIN20_n246DFElemCmpWth ;
   protected String[] IMSSOFFLIN20_A245DFElemIsFlt ;
   protected boolean[] IMSSOFFLIN20_n245DFElemIsFlt ;
   protected String[] IMSSOFFLIN20_A259DFElemFileType ;
   protected boolean[] IMSSOFFLIN20_n259DFElemFileType ;
   protected String[] IMSSOFFLIN20_A257DFElemRegexVal ;
   protected boolean[] IMSSOFFLIN20_n257DFElemRegexVal ;
   protected boolean[] IMSSOFFLIN20_A256DFElemAllowDlt ;
   protected boolean[] IMSSOFFLIN20_n256DFElemAllowDlt ;
   protected boolean[] IMSSOFFLIN20_A255DFElemAllowUpd ;
   protected boolean[] IMSSOFFLIN20_n255DFElemAllowUpd ;
   protected boolean[] IMSSOFFLIN20_A254DFElemAllowIns ;
   protected boolean[] IMSSOFFLIN20_n254DFElemAllowIns ;
   protected boolean[] IMSSOFFLIN20_A253DFElemUseBtns ;
   protected boolean[] IMSSOFFLIN20_n253DFElemUseBtns ;
   protected boolean[] IMSSOFFLIN20_A252DFElemIsOrd ;
   protected boolean[] IMSSOFFLIN20_n252DFElemIsOrd ;
   protected int[] IMSSOFFLIN20_A251DFElemMaxSuggRes ;
   protected boolean[] IMSSOFFLIN20_n251DFElemMaxSuggRes ;
   protected boolean[] IMSSOFFLIN20_A250DFElemForceSuggSel ;
   protected boolean[] IMSSOFFLIN20_n250DFElemForceSuggSel ;
   protected int[] IMSSOFFLIN20_A249DFElemMinCntCharSugg ;
   protected boolean[] IMSSOFFLIN20_n249DFElemMinCntCharSugg ;
   protected String[] IMSSOFFLIN20_A261DFElemDscPrgName ;
   protected String[] IMSSOFFLIN20_A248DFElemLoadPrgName ;
   protected boolean[] IMSSOFFLIN20_n248DFElemLoadPrgName ;
   protected String[] IMSSOFFLIN20_A270DFElemBtnPos ;
   protected boolean[] IMSSOFFLIN20_n270DFElemBtnPos ;
   protected String[] IMSSOFFLIN20_A271DFElemShwNbrLbl ;
   protected boolean[] IMSSOFFLIN20_n271DFElemShwNbrLbl ;
   protected boolean[] IMSSOFFLIN20_A269DFElemShwNbr ;
   protected boolean[] IMSSOFFLIN20_n269DFElemShwNbr ;
   protected boolean[] IMSSOFFLIN20_A264DFElemDateSel ;
   protected boolean[] IMSSOFFLIN20_n264DFElemDateSel ;
   protected boolean[] IMSSOFFLIN20_A247DFElemHasPmpt ;
   protected boolean[] IMSSOFFLIN20_n247DFElemHasPmpt ;
   protected String[] IMSSOFFLIN20_A183DFElemDftVal ;
   protected boolean[] IMSSOFFLIN20_n183DFElemDftVal ;
   protected int[] IMSSOFFLIN20_A244DFElemCntCols ;
   protected boolean[] IMSSOFFLIN20_n244DFElemCntCols ;
   protected int[] IMSSOFFLIN20_A243DFElemCntRows ;
   protected boolean[] IMSSOFFLIN20_n243DFElemCntRows ;
   protected int[] IMSSOFFLIN20_A242DFElemCntDec ;
   protected boolean[] IMSSOFFLIN20_n242DFElemCntDec ;
   protected int[] IMSSOFFLIN20_A258DFElemWth ;
   protected boolean[] IMSSOFFLIN20_n258DFElemWth ;
   protected int[] IMSSOFFLIN20_A239DFElemLen ;
   protected boolean[] IMSSOFFLIN20_n239DFElemLen ;
   protected String[] IMSSOFFLIN20_A199DFElemDsp ;
   protected boolean[] IMSSOFFLIN20_n199DFElemDsp ;
   protected String[] IMSSOFFLIN20_A181DFElemType ;
   protected int[] IMSSOFFLIN20_A111DFDomId ;
   protected boolean[] IMSSOFFLIN20_n111DFDomId ;
   protected String[] IMSSOFFLIN20_A195DFElemClsName ;
   protected boolean[] IMSSOFFLIN20_n195DFElemClsName ;
   protected String[] IMSSOFFLIN20_A238DFElemDsc ;
   protected boolean[] IMSSOFFLIN20_n238DFElemDsc ;
   protected String[] IMSSOFFLIN20_A151DFElemName ;
   protected java.util.UUID[] IMSSOFFLIN20_A114DFElemGuid ;
   protected int[] IMSSOFFLIN20_A89DFElemVer ;
   protected int[] IMSSOFFLIN20_A88DFElemId ;
   protected String[] IMSSOFFLIN21_A93DFFormRstVal ;
   protected int[] IMSSOFFLIN21_A92DFFormRstId ;
   protected int[] IMSSOFFLIN21_A87DFFormVer ;
   protected int[] IMSSOFFLIN21_A86DFFormId ;
   protected boolean[] IMSSOFFLIN22_A166DFUserRstPwdIni ;
   protected String[] IMSSOFFLIN22_A101DFUserRstVal ;
   protected int[] IMSSOFFLIN22_A100DFUserRstId ;
   protected String[] IMSSOFFLIN22_A99DFUserExtId ;
   protected boolean[] IMSSOFFLIN23_A319DFDomPrtDsc ;
   protected boolean[] IMSSOFFLIN23_n319DFDomPrtDsc ;
   protected String[] IMSSOFFLIN23_A226DFDomLblWth ;
   protected boolean[] IMSSOFFLIN23_n226DFDomLblWth ;
   protected String[] IMSSOFFLIN23_A222DFDomCmpWth ;
   protected boolean[] IMSSOFFLIN23_n222DFDomCmpWth ;
   protected String[] IMSSOFFLIN23_A221DFDomIsFlt ;
   protected boolean[] IMSSOFFLIN23_n221DFDomIsFlt ;
   protected String[] IMSSOFFLIN23_A224DFDomFileType ;
   protected boolean[] IMSSOFFLIN23_n224DFDomFileType ;
   protected String[] IMSSOFFLIN23_A220DFDomRegexVal ;
   protected boolean[] IMSSOFFLIN23_A216DFDomAllowDlt ;
   protected boolean[] IMSSOFFLIN23_n216DFDomAllowDlt ;
   protected boolean[] IMSSOFFLIN23_A215DFDomAllowUpd ;
   protected boolean[] IMSSOFFLIN23_n215DFDomAllowUpd ;
   protected boolean[] IMSSOFFLIN23_A214DFDomAllowIns ;
   protected boolean[] IMSSOFFLIN23_n214DFDomAllowIns ;
   protected boolean[] IMSSOFFLIN23_A213DFDomUseBtns ;
   protected boolean[] IMSSOFFLIN23_n213DFDomUseBtns ;
   protected boolean[] IMSSOFFLIN23_A212DFDomIsOrd ;
   protected boolean[] IMSSOFFLIN23_n212DFDomIsOrd ;
   protected int[] IMSSOFFLIN23_A210DFDomMaxSuggRes ;
   protected boolean[] IMSSOFFLIN23_n210DFDomMaxSuggRes ;
   protected boolean[] IMSSOFFLIN23_A209DFDomForceSuggSel ;
   protected boolean[] IMSSOFFLIN23_n209DFDomForceSuggSel ;
   protected int[] IMSSOFFLIN23_A208DFDomMinCntCharSugg ;
   protected boolean[] IMSSOFFLIN23_n208DFDomMinCntCharSugg ;
   protected String[] IMSSOFFLIN23_A211DFDomDftVal ;
   protected boolean[] IMSSOFFLIN23_n211DFDomDftVal ;
   protected int[] IMSSOFFLIN23_A219DFDomCntCols ;
   protected int[] IMSSOFFLIN23_A218DFDomCntRows ;
   protected int[] IMSSOFFLIN23_A217DFDomCntDec ;
   protected int[] IMSSOFFLIN23_A223DFDomWth ;
   protected int[] IMSSOFFLIN23_A207DFDomLen ;
   protected String[] IMSSOFFLIN23_A198DFDomDsp ;
   protected boolean[] IMSSOFFLIN23_n198DFDomDsp ;
   protected String[] IMSSOFFLIN23_A197DFDomType ;
   protected java.util.UUID[] IMSSOFFLIN23_A227DFDomGUID ;
   protected String[] IMSSOFFLIN23_A206DFDomDsc ;
   protected int[] IMSSOFFLIN23_A111DFDomId ;
   protected boolean[] IMSSOFFLIN23_n111DFDomId ;
   protected int[] IMSSOFFLIN24_A117DFSubElemFormPos ;
   protected boolean[] IMSSOFFLIN24_n117DFSubElemFormPos ;
   protected int[] IMSSOFFLIN24_A109DFSubElemFormElemVer ;
   protected int[] IMSSOFFLIN24_A108DFSubElemFormElemId ;
   protected int[] IMSSOFFLIN24_A89DFElemVer ;
   protected int[] IMSSOFFLIN24_A88DFElemId ;
   protected int[] IMSSOFFLIN24_A87DFFormVer ;
   protected int[] IMSSOFFLIN24_A86DFFormId ;
   protected int[] IMSSOFFLIN25_A120DFFilElemFormElemVer ;
   protected int[] IMSSOFFLIN25_A119DFFilElemFormElemId ;
   protected short[] IMSSOFFLIN25_A121DFFilElemFormPos ;
   protected int[] IMSSOFFLIN25_A118DFFilElemFormId ;
   protected int[] IMSSOFFLIN25_A89DFElemVer ;
   protected int[] IMSSOFFLIN25_A88DFElemId ;
   protected int[] IMSSOFFLIN25_A87DFFormVer ;
   protected int[] IMSSOFFLIN25_A86DFFormId ;
   protected short[] IMSSOFFLIN26_A288HospitalId ;
   protected boolean[] IMSSOFFLIN26_n288HospitalId ;
   protected String[] IMSSOFFLIN26_A36ServicioDescripcion ;
   protected short[] IMSSOFFLIN26_A6ServicioId ;
   protected int[] IMSSOFFLIN27_A105DFFormInstFormId ;
   protected String[] IMSSOFFLIN27_A141DFUplFileExt ;
   protected String[] IMSSOFFLIN27_A142DFUplFileName ;
   protected String[] IMSSOFFLIN27_A140DFUplFile ;
   protected String[] IMSSOFFLIN27_A91DFUplKey ;
   protected long[] IMSSOFFLIN27_A90DFFormInstId ;
   protected GxObjectCollection AV2ColDFFormInstId ;
   protected GxObjectCollection AV3ColPacienteNSSAgregado ;
   protected GxObjectCollection GXt_objcol_int3 ;
   protected GxObjectCollection GXv_objcol_int4[] ;
}

final  class imssofflinedatabase__default extends DataStoreHelperBase implements ILocalDataStoreHelper
{
   protected Object[] conditional_IMSSOFFLIN3( ModelContext context ,
                                               int remoteHandle ,
                                               com.genexus.internet.HttpContext httpContext ,
                                               String A75PacienteNSSAgregado ,
                                               GxObjectCollection AV3ColPacienteNSSAgregado ,
                                               String A81Matricula ,
                                               String AV4Matricula )
   {
      String sWhereString = "" ;
      String scmdbuf ;
      byte[] GXv_int9 ;
      GXv_int9 = new byte [1] ;
      Object[] GXv_Object10 ;
      GXv_Object10 = new Object [2] ;
      scmdbuf = "SELECT T2.PacienteNSSAgregado, T1.Matricula, T1.PacienteAgregado, T1.PacienteNSS" ;
      scmdbuf = scmdbuf + " FROM (PacienteMedicoOffline T1 INNER JOIN Paciente T2 ON T2.PacienteNSS = T1.PacienteNSS" ;
      scmdbuf = scmdbuf + " AND T2.PacienteAgregado = T1.PacienteAgregado)" ;
      scmdbuf = scmdbuf + " WHERE (RTRIM(LTRIM(T1.Matricula)) = ( ?))" ;
      scmdbuf = scmdbuf + " and (" + GXutil.toValueList("postgresql", AV3ColPacienteNSSAgregado, "T2.PacienteNSSAgregado IN (", ")") + ")" ;
      scmdbuf = scmdbuf + sWhereString ;
      scmdbuf = scmdbuf + " ORDER BY T1.PacienteNSS, T1.PacienteAgregado, T1.Matricula" ;
      GXv_Object10[0] = scmdbuf ;
      GXv_Object10[1] = GXv_int9 ;
      return GXv_Object10 ;
   }

   protected Object[] conditional_IMSSOFFLIN5( ModelContext context ,
                                               int remoteHandle ,
                                               com.genexus.internet.HttpContext httpContext ,
                                               String A75PacienteNSSAgregado ,
                                               GxObjectCollection AV3ColPacienteNSSAgregado )
   {
      String sWhereString = "" ;
      String scmdbuf ;
      Object[] GXv_Object12 ;
      GXv_Object12 = new Object [2] ;
      scmdbuf = "SELECT T2.PacienteNSSAgregado, T1.MMatricula, T1.MApMat, T1.MApPat, T1.MNombre, T1.MBMatricula," ;
      scmdbuf = scmdbuf + " T1.MBApMat, T1.MBApPat, T1.MBNombre, T1.JSMatricula, T1.JSApMat, T1.JSApPat, T1.JSNombre," ;
      scmdbuf = scmdbuf + " T1.DiagnosticoCirugiaFecha, T1.DiagnosticoCirugia, T1.Cama, T1.ServicioId, T1.DiagnosticoResumen," ;
      scmdbuf = scmdbuf + " T1.DiagnosticoComplemento, T1.DiagnosticoFechaAlta, T1.DiagnosticoFechaIngreso," ;
      scmdbuf = scmdbuf + " T1.CIE10Id, T1.PacienteAgregado, T1.PacienteNSS FROM (ExpedienteDiagnostico T1 INNER" ;
      scmdbuf = scmdbuf + " JOIN Paciente T2 ON T2.PacienteNSS = T1.PacienteNSS AND T2.PacienteAgregado = T1.PacienteAgregado)" ;
      scmdbuf = scmdbuf + " WHERE (" + GXutil.toValueList("postgresql", AV3ColPacienteNSSAgregado, "T2.PacienteNSSAgregado IN (", ")") + ")" ;
      scmdbuf = scmdbuf + sWhereString ;
      scmdbuf = scmdbuf + " ORDER BY T1.PacienteNSS, T1.PacienteAgregado, T1.CIE10Id" ;
      GXv_Object12[0] = scmdbuf ;
      return GXv_Object12 ;
   }

   protected Object[] conditional_IMSSOFFLIN8( ModelContext context ,
                                               int remoteHandle ,
                                               com.genexus.internet.HttpContext httpContext ,
                                               String A75PacienteNSSAgregado ,
                                               GxObjectCollection AV3ColPacienteNSSAgregado )
   {
      String sWhereString = "" ;
      String scmdbuf ;
      Object[] GXv_Object15 ;
      GXv_Object15 = new Object [2] ;
      scmdbuf = "SELECT T2.PacienteNSSAgregado, T1.DXAuxImagenImg_GXI, T1.DXAuxImagenExtension, T1.DXAuxImagenNombre," ;
      scmdbuf = scmdbuf + " T1.DXAuxImagenUserAlta, T1.DXAuxImagenFechaAlta, T1.DXAuxImagenImg, T1.DXAuxImagenId," ;
      scmdbuf = scmdbuf + " T1.CIE10Id, T1.PacienteAgregado, T1.PacienteNSS FROM (DXAuxImagen T1 INNER JOIN" ;
      scmdbuf = scmdbuf + " Paciente T2 ON T2.PacienteNSS = T1.PacienteNSS AND T2.PacienteAgregado = T1.PacienteAgregado)" ;
      scmdbuf = scmdbuf + " WHERE (" + GXutil.toValueList("postgresql", AV3ColPacienteNSSAgregado, "T2.PacienteNSSAgregado IN (", ")") + ")" ;
      scmdbuf = scmdbuf + sWhereString ;
      scmdbuf = scmdbuf + " ORDER BY T1.PacienteNSS, T1.PacienteAgregado, T1.CIE10Id, T1.DXAuxImagenId" ;
      GXv_Object15[0] = scmdbuf ;
      return GXv_Object15 ;
   }

   protected Object[] conditional_IMSSOFFLIN9( ModelContext context ,
                                               int remoteHandle ,
                                               com.genexus.internet.HttpContext httpContext ,
                                               String A75PacienteNSSAgregado ,
                                               GxObjectCollection AV3ColPacienteNSSAgregado )
   {
      String sWhereString = "" ;
      String scmdbuf ;
      Object[] GXv_Object18 ;
      GXv_Object18 = new Object [2] ;
      scmdbuf = "SELECT T2.PacienteNSSAgregado, T1.DXAuxDoctoNombre, T1.DXAuxDoctoExtension, T1.DXAuxDoctoUserAlta," ;
      scmdbuf = scmdbuf + " T1.DXAuxDoctoFechaAlta, T1.DXAuxDoctoDocumento, T1.DXAuxDoctoId, T1.CIE10Id, T1.PacienteAgregado," ;
      scmdbuf = scmdbuf + " T1.PacienteNSS FROM (DXAuxDocto T1 INNER JOIN Paciente T2 ON T2.PacienteNSS = T1.PacienteNSS" ;
      scmdbuf = scmdbuf + " AND T2.PacienteAgregado = T1.PacienteAgregado)" ;
      scmdbuf = scmdbuf + " WHERE (" + GXutil.toValueList("postgresql", AV3ColPacienteNSSAgregado, "T2.PacienteNSSAgregado IN (", ")") + ")" ;
      scmdbuf = scmdbuf + sWhereString ;
      scmdbuf = scmdbuf + " ORDER BY T1.PacienteNSS, T1.PacienteAgregado, T1.CIE10Id, T1.DXAuxDoctoId" ;
      GXv_Object18[0] = scmdbuf ;
      return GXv_Object18 ;
   }

   protected Object[] conditional_IMSSOFFLIN10( ModelContext context ,
                                                int remoteHandle ,
                                                com.genexus.internet.HttpContext httpContext ,
                                                String A75PacienteNSSAgregado ,
                                                GxObjectCollection AV3ColPacienteNSSAgregado )
   {
      String sWhereString = "" ;
      String scmdbuf ;
      Object[] GXv_Object21 ;
      GXv_Object21 = new Object [2] ;
      scmdbuf = "SELECT PacienteServicioId, PacienteDiagnosticoPhone, PacienteCie10Id, PAcienteFechaIngreso," ;
      scmdbuf = scmdbuf + " PacienteNSSAgregado, PacienteCama, PacienteDiagnosticoResumido, PacienteDiagnostico," ;
      scmdbuf = scmdbuf + " PacienteFechaNacimiento, PacienteNombreCompleto, PacienteReferencia, PacienteFamiliar," ;
      scmdbuf = scmdbuf + " PacienteTelefono, PacienteGenero, PacienteEdad, PacienteApMat, PacienteApPat, PacienteNombre," ;
      scmdbuf = scmdbuf + " PacienteAgregado, PacienteNSS FROM Paciente" ;
      scmdbuf = scmdbuf + " WHERE (" + GXutil.toValueList("postgresql", AV3ColPacienteNSSAgregado, "PacienteNSSAgregado IN (", ")") + ")" ;
      scmdbuf = scmdbuf + sWhereString ;
      scmdbuf = scmdbuf + " ORDER BY PacienteNSS, PacienteAgregado" ;
      GXv_Object21[0] = scmdbuf ;
      return GXv_Object21 ;
   }

   protected Object[] conditional_IMSSOFFLIN12( ModelContext context ,
                                                int remoteHandle ,
                                                com.genexus.internet.HttpContext httpContext ,
                                                long A90DFFormInstId ,
                                                GxObjectCollection AV2ColDFFormInstId )
   {
      String sWhereString = "" ;
      String scmdbuf ;
      Object[] GXv_Object24 ;
      GXv_Object24 = new Object [2] ;
      scmdbuf = "SELECT FormatoPacienteMedicoNombre, FormatoPacienteMedicoMatricula, DFFormInstId," ;
      scmdbuf = scmdbuf + " FormatoPacienteAgregado, FormatoPacienteNSS FROM FormatoPaciente" ;
      scmdbuf = scmdbuf + " WHERE (" + GXutil.toValueList("postgresql", AV2ColDFFormInstId, "DFFormInstId IN (", ")") + ")" ;
      scmdbuf = scmdbuf + sWhereString ;
      scmdbuf = scmdbuf + " ORDER BY FormatoPacienteNSS, FormatoPacienteAgregado, DFFormInstId" ;
      GXv_Object24[0] = scmdbuf ;
      return GXv_Object24 ;
   }

   protected Object[] conditional_IMSSOFFLIN15( ModelContext context ,
                                                int remoteHandle ,
                                                com.genexus.internet.HttpContext httpContext ,
                                                long A90DFFormInstId ,
                                                GxObjectCollection AV2ColDFFormInstId )
   {
      String sWhereString = "" ;
      String scmdbuf ;
      Object[] GXv_Object27 ;
      GXv_Object27 = new Object [2] ;
      scmdbuf = "SELECT DFElemFormInstFileName, DFElemFormInstFileType, DFElemFormInstBlob, DFElemFormInstVal," ;
      scmdbuf = scmdbuf + " DFElemVer, DFElemId, DFFormInstId FROM DFElemFormInst" ;
      scmdbuf = scmdbuf + " WHERE (" + GXutil.toValueList("postgresql", AV2ColDFFormInstId, "DFFormInstId IN (", ")") + ")" ;
      scmdbuf = scmdbuf + sWhereString ;
      scmdbuf = scmdbuf + " ORDER BY DFFormInstId, DFElemId, DFElemVer" ;
      GXv_Object27[0] = scmdbuf ;
      return GXv_Object27 ;
   }

   protected Object[] conditional_IMSSOFFLIN16( ModelContext context ,
                                                int remoteHandle ,
                                                com.genexus.internet.HttpContext httpContext ,
                                                long A90DFFormInstId ,
                                                GxObjectCollection AV2ColDFFormInstId )
   {
      String sWhereString = "" ;
      String scmdbuf ;
      Object[] GXv_Object30 ;
      GXv_Object30 = new Object [2] ;
      scmdbuf = "SELECT DFElemFormInstSubElemFileName, DFElemFormInstSubElemFileType, DFSubElemFormElemId," ;
      scmdbuf = scmdbuf + " DFSubElemFormElemVer, DFElemFormInstSubElemRow, DFElemFormInstSubElemVal, DFElemFormInstSubElemBlob," ;
      scmdbuf = scmdbuf + " DFElemFormInstSubElemId, DFElemVer, DFElemId, DFFormInstId FROM DFElemFormInstSubElem" ;
      scmdbuf = scmdbuf + " WHERE (" + GXutil.toValueList("postgresql", AV2ColDFFormInstId, "DFFormInstId IN (", ")") + ")" ;
      scmdbuf = scmdbuf + sWhereString ;
      scmdbuf = scmdbuf + " ORDER BY DFFormInstId, DFElemId, DFElemVer, DFElemFormInstSubElemId" ;
      GXv_Object30[0] = scmdbuf ;
      return GXv_Object30 ;
   }

   protected Object[] conditional_IMSSOFFLIN19( ModelContext context ,
                                                int remoteHandle ,
                                                com.genexus.internet.HttpContext httpContext ,
                                                long A90DFFormInstId ,
                                                GxObjectCollection AV2ColDFFormInstId )
   {
      String sWhereString = "" ;
      String scmdbuf ;
      Object[] GXv_Object33 ;
      GXv_Object33 = new Object [2] ;
      scmdbuf = "SELECT DFFormInstSignedPDF, DFFormInstSignedBy, DFFormInstDT, DFFormInstFormVer," ;
      scmdbuf = scmdbuf + " DFFormInstFormId, DFFormInstId FROM DFFormInst" ;
      scmdbuf = scmdbuf + " WHERE (" + GXutil.toValueList("postgresql", AV2ColDFFormInstId, "DFFormInstId IN (", ")") + ")" ;
      scmdbuf = scmdbuf + sWhereString ;
      scmdbuf = scmdbuf + " ORDER BY DFFormInstId" ;
      GXv_Object33[0] = scmdbuf ;
      return GXv_Object33 ;
   }

   protected Object[] conditional_IMSSOFFLIN27( ModelContext context ,
                                                int remoteHandle ,
                                                com.genexus.internet.HttpContext httpContext ,
                                                long A90DFFormInstId ,
                                                GxObjectCollection AV2ColDFFormInstId )
   {
      String sWhereString = "" ;
      String scmdbuf ;
      Object[] GXv_Object36 ;
      GXv_Object36 = new Object [2] ;
      scmdbuf = "SELECT DISTINCT NULL AS DFFormInstFormId, DFUplFileExt, DFUplFileName, DFUplFile," ;
      scmdbuf = scmdbuf + " DFUplKey, DFFormInstId FROM ( SELECT T2.DFFormInstFormId, T1.DFUplFileExt, T1.DFUplFileName," ;
      scmdbuf = scmdbuf + " T1.DFUplFile, T1.DFUplKey, T1.DFFormInstId FROM (DFUpl T1 INNER JOIN DFFormInst" ;
      scmdbuf = scmdbuf + " T2 ON T2.DFFormInstId = T1.DFFormInstId)" ;
      scmdbuf = scmdbuf + " WHERE (" + GXutil.toValueList("postgresql", AV2ColDFFormInstId, "T1.DFFormInstId IN (", ")") + ")" ;
      scmdbuf = scmdbuf + sWhereString ;
      scmdbuf = scmdbuf + " ORDER BY T1.DFFormInstId, T1.DFUplKey" ;
      scmdbuf = scmdbuf + ") DistinctT" ;
      GXv_Object36[0] = scmdbuf ;
      return GXv_Object36 ;
   }

   public Object [] getDynamicStatement( int cursor ,
                                         ModelContext context ,
                                         int remoteHandle ,
                                         com.genexus.internet.HttpContext httpContext ,
                                         Object [] dynConstraints )
   {
      switch ( cursor )
      {
            case 1 :
                  return conditional_IMSSOFFLIN3(context, remoteHandle, httpContext, (String)dynConstraints[0] , (GxObjectCollection)dynConstraints[1] , (String)dynConstraints[2] , (String)dynConstraints[3] );
            case 3 :
                  return conditional_IMSSOFFLIN5(context, remoteHandle, httpContext, (String)dynConstraints[0] , (GxObjectCollection)dynConstraints[1] );
            case 6 :
                  return conditional_IMSSOFFLIN8(context, remoteHandle, httpContext, (String)dynConstraints[0] , (GxObjectCollection)dynConstraints[1] );
            case 7 :
                  return conditional_IMSSOFFLIN9(context, remoteHandle, httpContext, (String)dynConstraints[0] , (GxObjectCollection)dynConstraints[1] );
            case 8 :
                  return conditional_IMSSOFFLIN10(context, remoteHandle, httpContext, (String)dynConstraints[0] , (GxObjectCollection)dynConstraints[1] );
            case 10 :
                  return conditional_IMSSOFFLIN12(context, remoteHandle, httpContext, ((Number) dynConstraints[0]).longValue() , (GxObjectCollection)dynConstraints[1] );
            case 13 :
                  return conditional_IMSSOFFLIN15(context, remoteHandle, httpContext, ((Number) dynConstraints[0]).longValue() , (GxObjectCollection)dynConstraints[1] );
            case 14 :
                  return conditional_IMSSOFFLIN16(context, remoteHandle, httpContext, ((Number) dynConstraints[0]).longValue() , (GxObjectCollection)dynConstraints[1] );
            case 17 :
                  return conditional_IMSSOFFLIN19(context, remoteHandle, httpContext, ((Number) dynConstraints[0]).longValue() , (GxObjectCollection)dynConstraints[1] );
            case 25 :
                  return conditional_IMSSOFFLIN27(context, remoteHandle, httpContext, ((Number) dynConstraints[0]).longValue() , (GxObjectCollection)dynConstraints[1] );
      }
      return super.getDynamicStatement(cursor, context, remoteHandle, httpContext, dynConstraints);
   }

   public Cursor[] getCursors( )
   {
      return new Cursor[] {
          new ForEachCursor("IMSSOFFLIN2", "SELECT MedicoDebeMostarTerm, MedicoDebeValidarDatos, MedicoUltimaActualizacion, MedicoMatricula, MedicoApellidoMaterno, MedicoApellidoPaterno, MedicoSegundoNombre, MedicoPrimerNombre, UserMedico FROM Medico WHERE UserMedico = ( ?) ORDER BY UserMedico ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,1,0,true )
         ,new ForEachCursor("IMSSOFFLIN3", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN4", "SELECT CIECodigo, CIE10Descripcion, CIE10Id FROM CIE10 ORDER BY CIE10Id ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN5", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN6", "SELECT nada, TextoDescripcion, TextoTitulo, TextoId FROM Texto ORDER BY TextoId ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN7", "SELECT DFParmIsMetaData, DFParmVal, DFParmName, DFParmId FROM DFParm ORDER BY DFParmId ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN8", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN9", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN10", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN11", "SELECT DFFormDsc, DFFormIsSD, DFFormRunDLT, DFFormHelpURL, DFFormPrefix, DFFormPmtHgh, DFFormPmtWth, DFFormAct, DFFormName, DFFormGuid, DFFormVer, DFFormId FROM DFForm ORDER BY DFFormId, DFFormVer ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN12", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN13", "SELECT ExtensionNombre, ExtensionTipo, ExtensionId FROM Extension ORDER BY ExtensionId ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN14", "SELECT DFElemFormReq, DFElemFormPrtPic, DFElemFormLoadRule, DFElemFormMetadata, DFElemFormShwNbr, DFElemFormDateSel, DFElemFormHasPmpt, DFElemFormIsFlt, DFElemFormCmpWth, DFElemFormLblWth, DFElemFormPrtShwNbr, DFElemFormPrtNumColSkip, DFElemFormPrtNumRowSkip, DFElemFormPrtAddRows, DFElemFormPrtName, DFElemFormIsVisPrt, DFElemFormIsVis, DFElemFormIsColap, DFElemFormAllowIns, DFElemFormAllowUpd, DFElemFormAllowDlt, DFElemFormInhType, DFElemFormPos, DFElemFormName, DFElemVer, DFElemId, DFFormVer, DFFormId FROM DFElemForm ORDER BY DFFormId, DFFormVer, DFElemId, DFElemVer ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN15", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN16", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN17", "SELECT DFTempFm, DFTempOutFm, DFTempAddParmPrgName, DFTempBlob, DFTempDsc, DFTempName, DFFormVer, DFFormId FROM DFTemp ORDER BY DFFormId, DFFormVer, DFTempName ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN18", "SELECT DFDomStaValOptDsc, DFDomStaValOptOrd, DFDomStaValOptCod, DFDomId FROM DFDomStaVals ORDER BY DFDomId, DFDomStaValOptCod ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN19", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN20", "SELECT DFElemReq, DFElemPrtPic, DFElemLoadRule, DFElemMetadata, DFElemIsColap, DFElemPrtShwNbr, DFElemPrtNumColSkip, DFElemPrtNumRowSkip, DFElemPrtAddRows, DFElemPrtName, DFElemIsVisPrt, DFElemIsVis, DFElemLblWth, DFElemCmpWth, DFElemIsFlt, DFElemFileType, DFElemRegexVal, DFElemAllowDlt, DFElemAllowUpd, DFElemAllowIns, DFElemUseBtns, DFElemIsOrd, DFElemMaxSuggRes, DFElemForceSuggSel, DFElemMinCntCharSugg, DFElemDscPrgName, DFElemLoadPrgName, DFElemBtnPos, DFElemShwNbrLbl, DFElemShwNbr, DFElemDateSel, DFElemHasPmpt, DFElemDftVal, DFElemCntCols, DFElemCntRows, DFElemCntDec, DFElemWth, DFElemLen, DFElemDsp, DFElemType, DFDomId, DFElemClsName, DFElemDsc, DFElemName, DFElemGuid, DFElemVer, DFElemId FROM DFElem ORDER BY DFElemId, DFElemVer ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN21", "SELECT DFFormRstVal, DFFormRstId, DFFormVer, DFFormId FROM DFFormRst ORDER BY DFFormId, DFFormVer, DFFormRstId, DFFormRstVal ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN22", "SELECT DFUserRstPwdIni, DFUserRstVal, DFUserRstId, DFUserExtId FROM DFUserRst ORDER BY DFUserExtId, DFUserRstId, DFUserRstVal ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN23", "SELECT DFDomPrtDsc, DFDomLblWth, DFDomCmpWth, DFDomIsFlt, DFDomFileType, DFDomRegexVal, DFDomAllowDlt, DFDomAllowUpd, DFDomAllowIns, DFDomUseBtns, DFDomIsOrd, DFDomMaxSuggRes, DFDomForceSuggSel, DFDomMinCntCharSugg, DFDomDftVal, DFDomCntCols, DFDomCntRows, DFDomCntDec, DFDomWth, DFDomLen, DFDomDsp, DFDomType, DFDomGUID, DFDomDsc, DFDomId FROM DFDom ORDER BY DFDomId ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN24", "SELECT DFSubElemFormPos, DFSubElemFormElemVer, DFSubElemFormElemId, DFElemVer, DFElemId, DFFormVer, DFFormId FROM DFSubElemForm ORDER BY DFFormId, DFFormVer, DFElemId, DFElemVer, DFSubElemFormElemId, DFSubElemFormElemVer ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN25", "SELECT DFFilElemFormElemVer, DFFilElemFormElemId, DFFilElemFormPos, DFFilElemFormId, DFElemVer, DFElemId, DFFormVer, DFFormId FROM DFFilElemForm ORDER BY DFFormId, DFFormVer, DFElemId, DFElemVer, DFFilElemFormId ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN26", "SELECT HospitalId, ServicioDescripcion, ServicioId FROM Servicio ORDER BY ServicioId ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN27", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
      };
   }

   public void getResults( int cursor ,
                           IFieldGetter rslt ,
                           Object[] buf ) throws SQLException
   {
      switch ( cursor )
      {
            case 0 :
               ((boolean[]) buf[0])[0] = rslt.getBoolean(1) ;
               ((boolean[]) buf[1])[0] = rslt.getBoolean(2) ;
               ((java.util.Date[]) buf[2])[0] = rslt.getGXDateTime(3) ;
               ((long[]) buf[3])[0] = rslt.getLong(4) ;
               ((boolean[]) buf[4])[0] = rslt.wasNull();
               ((String[]) buf[5])[0] = rslt.getString(5, 40) ;
               ((String[]) buf[6])[0] = rslt.getString(6, 40) ;
               ((String[]) buf[7])[0] = rslt.getString(7, 40) ;
               ((String[]) buf[8])[0] = rslt.getString(8, 40) ;
               ((String[]) buf[9])[0] = rslt.getString(9, 30) ;
               return;
            case 1 :
               ((String[]) buf[0])[0] = rslt.getVarchar(1) ;
               ((String[]) buf[1])[0] = rslt.getString(2, 20) ;
               ((String[]) buf[2])[0] = rslt.getString(3, 8) ;
               ((String[]) buf[3])[0] = rslt.getString(4, 11) ;
               return;
            case 2 :
               ((String[]) buf[0])[0] = rslt.getVarchar(1) ;
               ((String[]) buf[1])[0] = rslt.getVarchar(2) ;
               ((int[]) buf[2])[0] = rslt.getInt(3) ;
               return;
            case 3 :
               ((String[]) buf[0])[0] = rslt.getVarchar(1) ;
               ((long[]) buf[1])[0] = rslt.getLong(2) ;
               ((boolean[]) buf[2])[0] = rslt.wasNull();
               ((String[]) buf[3])[0] = rslt.getString(3, 40) ;
               ((boolean[]) buf[4])[0] = rslt.wasNull();
               ((String[]) buf[5])[0] = rslt.getString(4, 40) ;
               ((boolean[]) buf[6])[0] = rslt.wasNull();
               ((String[]) buf[7])[0] = rslt.getVarchar(5) ;
               ((boolean[]) buf[8])[0] = rslt.wasNull();
               ((long[]) buf[9])[0] = rslt.getLong(6) ;
               ((boolean[]) buf[10])[0] = rslt.wasNull();
               ((String[]) buf[11])[0] = rslt.getString(7, 40) ;
               ((boolean[]) buf[12])[0] = rslt.wasNull();
               ((String[]) buf[13])[0] = rslt.getString(8, 40) ;
               ((boolean[]) buf[14])[0] = rslt.wasNull();
               ((String[]) buf[15])[0] = rslt.getString(9, 40) ;
               ((boolean[]) buf[16])[0] = rslt.wasNull();
               ((long[]) buf[17])[0] = rslt.getLong(10) ;
               ((boolean[]) buf[18])[0] = rslt.wasNull();
               ((String[]) buf[19])[0] = rslt.getString(11, 40) ;
               ((boolean[]) buf[20])[0] = rslt.wasNull();
               ((String[]) buf[21])[0] = rslt.getString(12, 40) ;
               ((boolean[]) buf[22])[0] = rslt.wasNull();
               ((String[]) buf[23])[0] = rslt.getString(13, 40) ;
               ((boolean[]) buf[24])[0] = rslt.wasNull();
               ((java.util.Date[]) buf[25])[0] = rslt.getGXDateTime(14) ;
               ((boolean[]) buf[26])[0] = rslt.wasNull();
               ((String[]) buf[27])[0] = rslt.getLongVarchar(15) ;
               ((boolean[]) buf[28])[0] = rslt.wasNull();
               ((String[]) buf[29])[0] = rslt.getString(16, 6) ;
               ((boolean[]) buf[30])[0] = rslt.wasNull();
               ((short[]) buf[31])[0] = rslt.getShort(17) ;
               ((String[]) buf[32])[0] = rslt.getLongVarchar(18) ;
               ((boolean[]) buf[33])[0] = rslt.wasNull();
               ((String[]) buf[34])[0] = rslt.getLongVarchar(19) ;
               ((boolean[]) buf[35])[0] = rslt.wasNull();
               ((java.util.Date[]) buf[36])[0] = rslt.getGXDateTime(20) ;
               ((boolean[]) buf[37])[0] = rslt.wasNull();
               ((java.util.Date[]) buf[38])[0] = rslt.getGXDate(21) ;
               ((boolean[]) buf[39])[0] = rslt.wasNull();
               ((int[]) buf[40])[0] = rslt.getInt(22) ;
               ((String[]) buf[41])[0] = rslt.getString(23, 8) ;
               ((String[]) buf[42])[0] = rslt.getString(24, 11) ;
               return;
            case 4 :
               ((short[]) buf[0])[0] = rslt.getShort(1) ;
               ((String[]) buf[1])[0] = rslt.getLongVarchar(2) ;
               ((String[]) buf[2])[0] = rslt.getVarchar(3) ;
               ((short[]) buf[3])[0] = rslt.getShort(4) ;
               return;
            case 5 :
               ((boolean[]) buf[0])[0] = rslt.getBoolean(1) ;
               ((String[]) buf[1])[0] = rslt.getString(2, 200) ;
               ((String[]) buf[2])[0] = rslt.getString(3, 100) ;
               ((int[]) buf[3])[0] = rslt.getInt(4) ;
               return;
            case 6 :
               ((String[]) buf[0])[0] = rslt.getVarchar(1) ;
               ((String[]) buf[1])[0] = rslt.getMultimediaUri(2) ;
               ((String[]) buf[2])[0] = rslt.getString(3, 10) ;
               ((String[]) buf[3])[0] = rslt.getString(4, 40) ;
               ((String[]) buf[4])[0] = rslt.getString(5, 30) ;
               ((java.util.Date[]) buf[5])[0] = rslt.getGXDateTime(6) ;
               ((String[]) buf[6])[0] = rslt.getMultimediaFile(7, rslt.getVarchar(2)) ;
               ((short[]) buf[7])[0] = rslt.getShort(8) ;
               ((int[]) buf[8])[0] = rslt.getInt(9) ;
               ((String[]) buf[9])[0] = rslt.getString(10, 8) ;
               ((String[]) buf[10])[0] = rslt.getString(11, 11) ;
               return;
            case 7 :
               ((String[]) buf[0])[0] = rslt.getVarchar(1) ;
               ((String[]) buf[1])[0] = rslt.getString(2, 40) ;
               ((String[]) buf[2])[0] = rslt.getString(3, 10) ;
               ((String[]) buf[3])[0] = rslt.getString(4, 30) ;
               ((java.util.Date[]) buf[4])[0] = rslt.getGXDateTime(5) ;
               ((String[]) buf[5])[0] = rslt.getBLOBFile(6, rslt.getString(3, 10), rslt.getString(2, 40)) ;
               ((short[]) buf[6])[0] = rslt.getShort(7) ;
               ((int[]) buf[7])[0] = rslt.getInt(8) ;
               ((String[]) buf[8])[0] = rslt.getString(9, 8) ;
               ((String[]) buf[9])[0] = rslt.getString(10, 11) ;
               return;
            case 8 :
               ((short[]) buf[0])[0] = rslt.getShort(1) ;
               ((String[]) buf[1])[0] = rslt.getVarchar(2) ;
               ((int[]) buf[2])[0] = rslt.getInt(3) ;
               ((java.util.Date[]) buf[3])[0] = rslt.getGXDate(4) ;
               ((String[]) buf[4])[0] = rslt.getVarchar(5) ;
               ((String[]) buf[5])[0] = rslt.getString(6, 6) ;
               ((String[]) buf[6])[0] = rslt.getVarchar(7) ;
               ((String[]) buf[7])[0] = rslt.getVarchar(8) ;
               ((java.util.Date[]) buf[8])[0] = rslt.getGXDate(9) ;
               ((String[]) buf[9])[0] = rslt.getString(10, 150) ;
               ((String[]) buf[10])[0] = rslt.getString(11, 50) ;
               ((boolean[]) buf[11])[0] = rslt.wasNull();
               ((String[]) buf[12])[0] = rslt.getVarchar(12) ;
               ((boolean[]) buf[13])[0] = rslt.wasNull();
               ((String[]) buf[14])[0] = rslt.getString(13, 20) ;
               ((boolean[]) buf[15])[0] = rslt.wasNull();
               ((String[]) buf[16])[0] = rslt.getString(14, 1) ;
               ((boolean[]) buf[17])[0] = rslt.wasNull();
               ((short[]) buf[18])[0] = rslt.getShort(15) ;
               ((String[]) buf[19])[0] = rslt.getString(16, 40) ;
               ((boolean[]) buf[20])[0] = rslt.wasNull();
               ((String[]) buf[21])[0] = rslt.getString(17, 40) ;
               ((String[]) buf[22])[0] = rslt.getString(18, 40) ;
               ((String[]) buf[23])[0] = rslt.getString(19, 8) ;
               ((String[]) buf[24])[0] = rslt.getString(20, 11) ;
               return;
            case 9 :
               ((String[]) buf[0])[0] = rslt.getVarchar(1) ;
               ((boolean[]) buf[1])[0] = rslt.getBoolean(2) ;
               ((boolean[]) buf[2])[0] = rslt.getBoolean(3) ;
               ((String[]) buf[3])[0] = rslt.getVarchar(4) ;
               ((String[]) buf[4])[0] = rslt.getVarchar(5) ;
               ((int[]) buf[5])[0] = rslt.getInt(6) ;
               ((boolean[]) buf[6])[0] = rslt.wasNull();
               ((int[]) buf[7])[0] = rslt.getInt(7) ;
               ((boolean[]) buf[8])[0] = rslt.wasNull();
               ((boolean[]) buf[9])[0] = rslt.getBoolean(8) ;
               ((String[]) buf[10])[0] = rslt.getString(9, 100) ;
               ((java.util.UUID[]) buf[11])[0] = rslt.getGUID(10) ;
               ((int[]) buf[12])[0] = rslt.getInt(11) ;
               ((int[]) buf[13])[0] = rslt.getInt(12) ;
               return;
            case 10 :
               ((String[]) buf[0])[0] = rslt.getVarchar(1) ;
               ((long[]) buf[1])[0] = rslt.getLong(2) ;
               ((long[]) buf[2])[0] = rslt.getLong(3) ;
               ((String[]) buf[3])[0] = rslt.getString(4, 8) ;
               ((String[]) buf[4])[0] = rslt.getString(5, 11) ;
               return;
            case 11 :
               ((String[]) buf[0])[0] = rslt.getString(1, 40) ;
               ((short[]) buf[1])[0] = rslt.getShort(2) ;
               ((short[]) buf[2])[0] = rslt.getShort(3) ;
               return;
            case 12 :
               ((boolean[]) buf[0])[0] = rslt.getBoolean(1) ;
               ((String[]) buf[1])[0] = rslt.getVarchar(2) ;
               ((String[]) buf[2])[0] = rslt.getVarchar(3) ;
               ((boolean[]) buf[3])[0] = rslt.wasNull();
               ((String[]) buf[4])[0] = rslt.getVarchar(4) ;
               ((boolean[]) buf[5])[0] = rslt.wasNull();
               ((boolean[]) buf[6])[0] = rslt.getBoolean(5) ;
               ((boolean[]) buf[7])[0] = rslt.wasNull();
               ((boolean[]) buf[8])[0] = rslt.getBoolean(6) ;
               ((boolean[]) buf[9])[0] = rslt.wasNull();
               ((boolean[]) buf[10])[0] = rslt.getBoolean(7) ;
               ((boolean[]) buf[11])[0] = rslt.wasNull();
               ((String[]) buf[12])[0] = rslt.getString(8, 20) ;
               ((boolean[]) buf[13])[0] = rslt.wasNull();
               ((String[]) buf[14])[0] = rslt.getString(9, 20) ;
               ((boolean[]) buf[15])[0] = rslt.wasNull();
               ((String[]) buf[16])[0] = rslt.getString(10, 20) ;
               ((boolean[]) buf[17])[0] = rslt.wasNull();
               ((boolean[]) buf[18])[0] = rslt.getBoolean(11) ;
               ((int[]) buf[19])[0] = rslt.getInt(12) ;
               ((int[]) buf[20])[0] = rslt.getInt(13) ;
               ((boolean[]) buf[21])[0] = rslt.getBoolean(14) ;
               ((String[]) buf[22])[0] = rslt.getString(15, 100) ;
               ((boolean[]) buf[23])[0] = rslt.getBoolean(16) ;
               ((boolean[]) buf[24])[0] = rslt.getBoolean(17) ;
               ((boolean[]) buf[25])[0] = rslt.getBoolean(18) ;
               ((boolean[]) buf[26])[0] = rslt.getBoolean(19) ;
               ((boolean[]) buf[27])[0] = rslt.wasNull();
               ((boolean[]) buf[28])[0] = rslt.getBoolean(20) ;
               ((boolean[]) buf[29])[0] = rslt.wasNull();
               ((boolean[]) buf[30])[0] = rslt.getBoolean(21) ;
               ((boolean[]) buf[31])[0] = rslt.wasNull();
               ((String[]) buf[32])[0] = rslt.getString(22, 1) ;
               ((int[]) buf[33])[0] = rslt.getInt(23) ;
               ((String[]) buf[34])[0] = rslt.getString(24, 100) ;
               ((int[]) buf[35])[0] = rslt.getInt(25) ;
               ((int[]) buf[36])[0] = rslt.getInt(26) ;
               ((int[]) buf[37])[0] = rslt.getInt(27) ;
               ((int[]) buf[38])[0] = rslt.getInt(28) ;
               return;
            case 13 :
               ((String[]) buf[0])[0] = rslt.getString(1, 200) ;
               ((boolean[]) buf[1])[0] = rslt.wasNull();
               ((String[]) buf[2])[0] = rslt.getString(2, 20) ;
               ((boolean[]) buf[3])[0] = rslt.wasNull();
               ((String[]) buf[4])[0] = rslt.getBLOBFile(3, rslt.getString(2, 20), rslt.getString(1, 200)) ;
               ((boolean[]) buf[5])[0] = rslt.wasNull();
               ((String[]) buf[6])[0] = rslt.getVarchar(4) ;
               ((boolean[]) buf[7])[0] = rslt.wasNull();
               ((int[]) buf[8])[0] = rslt.getInt(5) ;
               ((int[]) buf[9])[0] = rslt.getInt(6) ;
               ((long[]) buf[10])[0] = rslt.getLong(7) ;
               return;
            case 14 :
               ((String[]) buf[0])[0] = rslt.getString(1, 200) ;
               ((boolean[]) buf[1])[0] = rslt.wasNull();
               ((String[]) buf[2])[0] = rslt.getString(2, 20) ;
               ((boolean[]) buf[3])[0] = rslt.wasNull();
               ((int[]) buf[4])[0] = rslt.getInt(3) ;
               ((int[]) buf[5])[0] = rslt.getInt(4) ;
               ((int[]) buf[6])[0] = rslt.getInt(5) ;
               ((String[]) buf[7])[0] = rslt.getVarchar(6) ;
               ((boolean[]) buf[8])[0] = rslt.wasNull();
               ((String[]) buf[9])[0] = rslt.getBLOBFile(7, rslt.getString(2, 20), rslt.getString(1, 200)) ;
               ((boolean[]) buf[10])[0] = rslt.wasNull();
               ((int[]) buf[11])[0] = rslt.getInt(8) ;
               ((int[]) buf[12])[0] = rslt.getInt(9) ;
               ((int[]) buf[13])[0] = rslt.getInt(10) ;
               ((long[]) buf[14])[0] = rslt.getLong(11) ;
               return;
            case 15 :
               ((String[]) buf[0])[0] = rslt.getString(1, 1) ;
               ((String[]) buf[1])[0] = rslt.getString(2, 1) ;
               ((String[]) buf[2])[0] = rslt.getVarchar(3) ;
               ((String[]) buf[3])[0] = rslt.getBLOBFile(4, "tmp", "") ;
               ((String[]) buf[4])[0] = rslt.getVarchar(5) ;
               ((String[]) buf[5])[0] = rslt.getString(6, 100) ;
               ((int[]) buf[6])[0] = rslt.getInt(7) ;
               ((int[]) buf[7])[0] = rslt.getInt(8) ;
               return;
            case 16 :
               ((String[]) buf[0])[0] = rslt.getString(1, 200) ;
               ((int[]) buf[1])[0] = rslt.getInt(2) ;
               ((String[]) buf[2])[0] = rslt.getString(3, 200) ;
               ((int[]) buf[3])[0] = rslt.getInt(4) ;
               return;
            case 17 :
               ((String[]) buf[0])[0] = rslt.getBLOBFile(1, "tmp", "") ;
               ((boolean[]) buf[1])[0] = rslt.wasNull();
               ((String[]) buf[2])[0] = rslt.getVarchar(2) ;
               ((boolean[]) buf[3])[0] = rslt.wasNull();
               ((java.util.Date[]) buf[4])[0] = rslt.getGXDateTime(3) ;
               ((int[]) buf[5])[0] = rslt.getInt(4) ;
               ((int[]) buf[6])[0] = rslt.getInt(5) ;
               ((long[]) buf[7])[0] = rslt.getLong(6) ;
               return;
            case 18 :
               ((boolean[]) buf[0])[0] = rslt.getBoolean(1) ;
               ((String[]) buf[1])[0] = rslt.getVarchar(2) ;
               ((String[]) buf[2])[0] = rslt.getVarchar(3) ;
               ((boolean[]) buf[3])[0] = rslt.wasNull();
               ((String[]) buf[4])[0] = rslt.getVarchar(4) ;
               ((boolean[]) buf[5])[0] = rslt.wasNull();
               ((boolean[]) buf[6])[0] = rslt.getBoolean(5) ;
               ((boolean[]) buf[7])[0] = rslt.getBoolean(6) ;
               ((int[]) buf[8])[0] = rslt.getInt(7) ;
               ((int[]) buf[9])[0] = rslt.getInt(8) ;
               ((boolean[]) buf[10])[0] = rslt.getBoolean(9) ;
               ((String[]) buf[11])[0] = rslt.getString(10, 100) ;
               ((boolean[]) buf[12])[0] = rslt.getBoolean(11) ;
               ((boolean[]) buf[13])[0] = rslt.getBoolean(12) ;
               ((String[]) buf[14])[0] = rslt.getString(13, 20) ;
               ((boolean[]) buf[15])[0] = rslt.wasNull();
               ((String[]) buf[16])[0] = rslt.getString(14, 20) ;
               ((boolean[]) buf[17])[0] = rslt.wasNull();
               ((String[]) buf[18])[0] = rslt.getString(15, 20) ;
               ((boolean[]) buf[19])[0] = rslt.wasNull();
               ((String[]) buf[20])[0] = rslt.getString(16, 20) ;
               ((boolean[]) buf[21])[0] = rslt.wasNull();
               ((String[]) buf[22])[0] = rslt.getString(17, 200) ;
               ((boolean[]) buf[23])[0] = rslt.wasNull();
               ((boolean[]) buf[24])[0] = rslt.getBoolean(18) ;
               ((boolean[]) buf[25])[0] = rslt.wasNull();
               ((boolean[]) buf[26])[0] = rslt.getBoolean(19) ;
               ((boolean[]) buf[27])[0] = rslt.wasNull();
               ((boolean[]) buf[28])[0] = rslt.getBoolean(20) ;
               ((boolean[]) buf[29])[0] = rslt.wasNull();
               ((boolean[]) buf[30])[0] = rslt.getBoolean(21) ;
               ((boolean[]) buf[31])[0] = rslt.wasNull();
               ((boolean[]) buf[32])[0] = rslt.getBoolean(22) ;
               ((boolean[]) buf[33])[0] = rslt.wasNull();
               ((int[]) buf[34])[0] = rslt.getInt(23) ;
               ((boolean[]) buf[35])[0] = rslt.wasNull();
               ((boolean[]) buf[36])[0] = rslt.getBoolean(24) ;
               ((boolean[]) buf[37])[0] = rslt.wasNull();
               ((int[]) buf[38])[0] = rslt.getInt(25) ;
               ((boolean[]) buf[39])[0] = rslt.wasNull();
               ((String[]) buf[40])[0] = rslt.getVarchar(26) ;
               ((String[]) buf[41])[0] = rslt.getVarchar(27) ;
               ((boolean[]) buf[42])[0] = rslt.wasNull();
               ((String[]) buf[43])[0] = rslt.getString(28, 20) ;
               ((boolean[]) buf[44])[0] = rslt.wasNull();
               ((String[]) buf[45])[0] = rslt.getString(29, 20) ;
               ((boolean[]) buf[46])[0] = rslt.wasNull();
               ((boolean[]) buf[47])[0] = rslt.getBoolean(30) ;
               ((boolean[]) buf[48])[0] = rslt.wasNull();
               ((boolean[]) buf[49])[0] = rslt.getBoolean(31) ;
               ((boolean[]) buf[50])[0] = rslt.wasNull();
               ((boolean[]) buf[51])[0] = rslt.getBoolean(32) ;
               ((boolean[]) buf[52])[0] = rslt.wasNull();
               ((String[]) buf[53])[0] = rslt.getString(33, 200) ;
               ((boolean[]) buf[54])[0] = rslt.wasNull();
               ((int[]) buf[55])[0] = rslt.getInt(34) ;
               ((boolean[]) buf[56])[0] = rslt.wasNull();
               ((int[]) buf[57])[0] = rslt.getInt(35) ;
               ((boolean[]) buf[58])[0] = rslt.wasNull();
               ((int[]) buf[59])[0] = rslt.getInt(36) ;
               ((boolean[]) buf[60])[0] = rslt.wasNull();
               ((int[]) buf[61])[0] = rslt.getInt(37) ;
               ((boolean[]) buf[62])[0] = rslt.wasNull();
               ((int[]) buf[63])[0] = rslt.getInt(38) ;
               ((boolean[]) buf[64])[0] = rslt.wasNull();
               ((String[]) buf[65])[0] = rslt.getString(39, 20) ;
               ((boolean[]) buf[66])[0] = rslt.wasNull();
               ((String[]) buf[67])[0] = rslt.getString(40, 20) ;
               ((int[]) buf[68])[0] = rslt.getInt(41) ;
               ((boolean[]) buf[69])[0] = rslt.wasNull();
               ((String[]) buf[70])[0] = rslt.getString(42, 100) ;
               ((boolean[]) buf[71])[0] = rslt.wasNull();
               ((String[]) buf[72])[0] = rslt.getVarchar(43) ;
               ((boolean[]) buf[73])[0] = rslt.wasNull();
               ((String[]) buf[74])[0] = rslt.getString(44, 100) ;
               ((java.util.UUID[]) buf[75])[0] = rslt.getGUID(45) ;
               ((int[]) buf[76])[0] = rslt.getInt(46) ;
               ((int[]) buf[77])[0] = rslt.getInt(47) ;
               return;
            case 19 :
               ((String[]) buf[0])[0] = rslt.getString(1, 200) ;
               ((int[]) buf[1])[0] = rslt.getInt(2) ;
               ((int[]) buf[2])[0] = rslt.getInt(3) ;
               ((int[]) buf[3])[0] = rslt.getInt(4) ;
               return;
            case 20 :
               ((boolean[]) buf[0])[0] = rslt.getBoolean(1) ;
               ((String[]) buf[1])[0] = rslt.getString(2, 200) ;
               ((int[]) buf[2])[0] = rslt.getInt(3) ;
               ((String[]) buf[3])[0] = rslt.getVarchar(4) ;
               return;
            case 21 :
               ((boolean[]) buf[0])[0] = rslt.getBoolean(1) ;
               ((boolean[]) buf[1])[0] = rslt.wasNull();
               ((String[]) buf[2])[0] = rslt.getString(2, 20) ;
               ((boolean[]) buf[3])[0] = rslt.wasNull();
               ((String[]) buf[4])[0] = rslt.getString(3, 20) ;
               ((boolean[]) buf[5])[0] = rslt.wasNull();
               ((String[]) buf[6])[0] = rslt.getString(4, 20) ;
               ((boolean[]) buf[7])[0] = rslt.wasNull();
               ((String[]) buf[8])[0] = rslt.getString(5, 20) ;
               ((boolean[]) buf[9])[0] = rslt.wasNull();
               ((String[]) buf[10])[0] = rslt.getString(6, 200) ;
               ((boolean[]) buf[11])[0] = rslt.getBoolean(7) ;
               ((boolean[]) buf[12])[0] = rslt.wasNull();
               ((boolean[]) buf[13])[0] = rslt.getBoolean(8) ;
               ((boolean[]) buf[14])[0] = rslt.wasNull();
               ((boolean[]) buf[15])[0] = rslt.getBoolean(9) ;
               ((boolean[]) buf[16])[0] = rslt.wasNull();
               ((boolean[]) buf[17])[0] = rslt.getBoolean(10) ;
               ((boolean[]) buf[18])[0] = rslt.wasNull();
               ((boolean[]) buf[19])[0] = rslt.getBoolean(11) ;
               ((boolean[]) buf[20])[0] = rslt.wasNull();
               ((int[]) buf[21])[0] = rslt.getInt(12) ;
               ((boolean[]) buf[22])[0] = rslt.wasNull();
               ((boolean[]) buf[23])[0] = rslt.getBoolean(13) ;
               ((boolean[]) buf[24])[0] = rslt.wasNull();
               ((int[]) buf[25])[0] = rslt.getInt(14) ;
               ((boolean[]) buf[26])[0] = rslt.wasNull();
               ((String[]) buf[27])[0] = rslt.getString(15, 200) ;
               ((boolean[]) buf[28])[0] = rslt.wasNull();
               ((int[]) buf[29])[0] = rslt.getInt(16) ;
               ((int[]) buf[30])[0] = rslt.getInt(17) ;
               ((int[]) buf[31])[0] = rslt.getInt(18) ;
               ((int[]) buf[32])[0] = rslt.getInt(19) ;
               ((int[]) buf[33])[0] = rslt.getInt(20) ;
               ((String[]) buf[34])[0] = rslt.getString(21, 20) ;
               ((boolean[]) buf[35])[0] = rslt.wasNull();
               ((String[]) buf[36])[0] = rslt.getString(22, 20) ;
               ((java.util.UUID[]) buf[37])[0] = rslt.getGUID(23) ;
               ((String[]) buf[38])[0] = rslt.getString(24, 60) ;
               ((int[]) buf[39])[0] = rslt.getInt(25) ;
               return;
            case 22 :
               ((int[]) buf[0])[0] = rslt.getInt(1) ;
               ((boolean[]) buf[1])[0] = rslt.wasNull();
               ((int[]) buf[2])[0] = rslt.getInt(2) ;
               ((int[]) buf[3])[0] = rslt.getInt(3) ;
               ((int[]) buf[4])[0] = rslt.getInt(4) ;
               ((int[]) buf[5])[0] = rslt.getInt(5) ;
               ((int[]) buf[6])[0] = rslt.getInt(6) ;
               ((int[]) buf[7])[0] = rslt.getInt(7) ;
               return;
            case 23 :
               ((int[]) buf[0])[0] = rslt.getInt(1) ;
               ((int[]) buf[1])[0] = rslt.getInt(2) ;
               ((short[]) buf[2])[0] = rslt.getShort(3) ;
               ((int[]) buf[3])[0] = rslt.getInt(4) ;
               ((int[]) buf[4])[0] = rslt.getInt(5) ;
               ((int[]) buf[5])[0] = rslt.getInt(6) ;
               ((int[]) buf[6])[0] = rslt.getInt(7) ;
               ((int[]) buf[7])[0] = rslt.getInt(8) ;
               return;
            case 24 :
               ((short[]) buf[0])[0] = rslt.getShort(1) ;
               ((boolean[]) buf[1])[0] = rslt.wasNull();
               ((String[]) buf[2])[0] = rslt.getString(2, 30) ;
               ((short[]) buf[3])[0] = rslt.getShort(3) ;
               return;
            case 25 :
               ((int[]) buf[0])[0] = rslt.getInt(1) ;
               ((String[]) buf[1])[0] = rslt.getString(2, 20) ;
               ((String[]) buf[2])[0] = rslt.getString(3, 200) ;
               ((String[]) buf[3])[0] = rslt.getBLOBFile(4, "tmp", "") ;
               ((String[]) buf[4])[0] = rslt.getString(5, 20) ;
               ((long[]) buf[5])[0] = rslt.getLong(6) ;
               return;
      }
   }

   public void setParameters( int cursor ,
                              IFieldSetter stmt ,
                              Object[] parms ) throws SQLException
   {
      short sIdx ;
      switch ( cursor )
      {
            case 0 :
               stmt.setString(1, (String)parms[0], 30);
               return;
            case 1 :
               sIdx = (short)(0) ;
               if ( ((Number) parms[0]).byteValue() == 0 )
               {
                  sIdx = (short)(sIdx+1) ;
                  stmt.setString(sIdx, (String)parms[1], 20);
               }
               return;
      }
   }

}

