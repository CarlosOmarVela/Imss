# Imss
comparar

/*
               File: IMSSOfflineDatabase
        Description: IMSSOffline Database
             Author: GeneXus Java Generator version 10_3_5-95299
       Generated on: May 4, 2016 16:37:8.95
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
      /* Execute user event: e11012 */
      e11012 ();
      if ( returnInSub )
      {
         returnInSub = true;
         cleanup();
         if (true) return;
      }
   }

   public void e11012( )
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
         A341FecBajaMed = IMSSOFFLIN2_A341FecBajaMed[0] ;
         n341FecBajaMed = IMSSOFFLIN2_n341FecBajaMed[0] ;
         A303MedDebMosTerm = IMSSOFFLIN2_A303MedDebMosTerm[0] ;
         n303MedDebMosTerm = IMSSOFFLIN2_n303MedDebMosTerm[0] ;
         A295MedDebValDat = IMSSOFFLIN2_A295MedDebValDat[0] ;
         A293MedUltAct = IMSSOFFLIN2_A293MedUltAct[0] ;
         A340MedCedProf = IMSSOFFLIN2_A340MedCedProf[0] ;
         A291MedApMat = IMSSOFFLIN2_A291MedApMat[0] ;
         A290MedApPat = IMSSOFFLIN2_A290MedApPat[0] ;
         A288MedNom = IMSSOFFLIN2_A288MedNom[0] ;
         A64UserMed = IMSSOFFLIN2_A64UserMed[0] ;
         A65MedMatricula = IMSSOFFLIN2_A65MedMatricula[0] ;
         gxsyncline.add(GXutil.dateToCharREST( A341FecBajaMed));
         gxsyncline.add(GXutil.rtrim( A291MedApMat));
         gxsyncline.add(GXutil.rtrim( A290MedApPat));
         gxsyncline.add(GXutil.rtrim( A340MedCedProf));
         gxsyncline.add(GXutil.booltostr( A303MedDebMosTerm));
         gxsyncline.add(GXutil.booltostr( A295MedDebValDat));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A65MedMatricula, (byte)(10), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A65MedMatricula, (byte)(10), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A288MedNom));
         gxsyncline.add(GXutil.timeToCharREST( A293MedUltAct));
         gxsyncline.add(GXutil.rtrim( A64UserMed));
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
         pr_default.readNext(0);
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
                                           A133PacienteNSSAgregado ,
                                           AV3ColPacienteNSSAgregado ,
                                           A8Matricula ,
                                           AV4Matricula },
                                           new int[] {
                                           TypeConstants.STRING, TypeConstants.OBJECT_COLLECTION, TypeConstants.STRING, TypeConstants.STRING
                                           }
      });
      /* Using cursor IMSSOFFLIN3 */
      pr_default.execute(1, new Object[] {AV4Matricula});
      while ( (pr_default.getStatus(1) != 101) )
      {
         A133PacienteNSSAgregado = IMSSOFFLIN3_A133PacienteNSSAgregado[0] ;
         A8Matricula = IMSSOFFLIN3_A8Matricula[0] ;
         A3PacienteAgregado = IMSSOFFLIN3_A3PacienteAgregado[0] ;
         A2PacienteNSS = IMSSOFFLIN3_A2PacienteNSS[0] ;
         A133PacienteNSSAgregado = IMSSOFFLIN3_A133PacienteNSSAgregado[0] ;
         gxsyncline.add(GXutil.rtrim( A8Matricula));
         gxsynchashkey.add(GXutil.rtrim( A8Matricula));
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
      /* Using cursor IMSSOFFLIN4 */
      pr_default.execute(2);
      while ( (pr_default.getStatus(2) != 101) )
      {
         A167DFParmIsMetaData = IMSSOFFLIN4_A167DFParmIsMetaData[0] ;
         A166DFParmVal = IMSSOFFLIN4_A166DFParmVal[0] ;
         A165DFParmName = IMSSOFFLIN4_A165DFParmName[0] ;
         A25DFParmId = IMSSOFFLIN4_A25DFParmId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A25DFParmId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A25DFParmId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.booltostr( A167DFParmIsMetaData));
         gxsyncline.add(GXutil.rtrim( A165DFParmName));
         gxsyncline.add(GXutil.rtrim( A166DFParmVal));
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
      /* Using cursor IMSSOFFLIN5 */
      pr_default.execute(3);
      while ( (pr_default.getStatus(3) != 101) )
      {
         A76CIE10Descripcion = IMSSOFFLIN5_A76CIE10Descripcion[0] ;
         A127CIECodigo = IMSSOFFLIN5_A127CIECodigo[0] ;
         A1CIE10Id = IMSSOFFLIN5_A1CIE10Id[0] ;
         gxsyncline.add(A76CIE10Descripcion);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(A127CIECodigo);
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
      pr_default.dynParam(4, new Object[]{ new Object[]{
                                           A133PacienteNSSAgregado ,
                                           AV3ColPacienteNSSAgregado },
                                           new int[] {
                                           TypeConstants.STRING, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN6 */
      pr_default.execute(4);
      while ( (pr_default.getStatus(4) != 101) )
      {
         A133PacienteNSSAgregado = IMSSOFFLIN6_A133PacienteNSSAgregado[0] ;
         A102MMatricula = IMSSOFFLIN6_A102MMatricula[0] ;
         n102MMatricula = IMSSOFFLIN6_n102MMatricula[0] ;
         A101MApMat = IMSSOFFLIN6_A101MApMat[0] ;
         n101MApMat = IMSSOFFLIN6_n101MApMat[0] ;
         A100MApPat = IMSSOFFLIN6_A100MApPat[0] ;
         n100MApPat = IMSSOFFLIN6_n100MApPat[0] ;
         A99MNombre = IMSSOFFLIN6_A99MNombre[0] ;
         n99MNombre = IMSSOFFLIN6_n99MNombre[0] ;
         A98MBMatricula = IMSSOFFLIN6_A98MBMatricula[0] ;
         n98MBMatricula = IMSSOFFLIN6_n98MBMatricula[0] ;
         A97MBApMat = IMSSOFFLIN6_A97MBApMat[0] ;
         n97MBApMat = IMSSOFFLIN6_n97MBApMat[0] ;
         A96MBApPat = IMSSOFFLIN6_A96MBApPat[0] ;
         n96MBApPat = IMSSOFFLIN6_n96MBApPat[0] ;
         A95MBNombre = IMSSOFFLIN6_A95MBNombre[0] ;
         n95MBNombre = IMSSOFFLIN6_n95MBNombre[0] ;
         A94JSMatricula = IMSSOFFLIN6_A94JSMatricula[0] ;
         n94JSMatricula = IMSSOFFLIN6_n94JSMatricula[0] ;
         A93JSApMat = IMSSOFFLIN6_A93JSApMat[0] ;
         n93JSApMat = IMSSOFFLIN6_n93JSApMat[0] ;
         A92JSApPat = IMSSOFFLIN6_A92JSApPat[0] ;
         n92JSApPat = IMSSOFFLIN6_n92JSApPat[0] ;
         A91JSNombre = IMSSOFFLIN6_A91JSNombre[0] ;
         n91JSNombre = IMSSOFFLIN6_n91JSNombre[0] ;
         A90DiagnosticoCirugiaFecha = IMSSOFFLIN6_A90DiagnosticoCirugiaFecha[0] ;
         n90DiagnosticoCirugiaFecha = IMSSOFFLIN6_n90DiagnosticoCirugiaFecha[0] ;
         A89DiagnosticoCirugia = IMSSOFFLIN6_A89DiagnosticoCirugia[0] ;
         n89DiagnosticoCirugia = IMSSOFFLIN6_n89DiagnosticoCirugia[0] ;
         A88Cama = IMSSOFFLIN6_A88Cama[0] ;
         n88Cama = IMSSOFFLIN6_n88Cama[0] ;
         A6ServicioId = IMSSOFFLIN6_A6ServicioId[0] ;
         A86DiagnosticoComplemento = IMSSOFFLIN6_A86DiagnosticoComplemento[0] ;
         n86DiagnosticoComplemento = IMSSOFFLIN6_n86DiagnosticoComplemento[0] ;
         A87DiagnosticoResumen = IMSSOFFLIN6_A87DiagnosticoResumen[0] ;
         n87DiagnosticoResumen = IMSSOFFLIN6_n87DiagnosticoResumen[0] ;
         A103DiagnosticoFechaAlta = IMSSOFFLIN6_A103DiagnosticoFechaAlta[0] ;
         n103DiagnosticoFechaAlta = IMSSOFFLIN6_n103DiagnosticoFechaAlta[0] ;
         A85DiagnosticoFechaIngreso = IMSSOFFLIN6_A85DiagnosticoFechaIngreso[0] ;
         n85DiagnosticoFechaIngreso = IMSSOFFLIN6_n85DiagnosticoFechaIngreso[0] ;
         A1CIE10Id = IMSSOFFLIN6_A1CIE10Id[0] ;
         A3PacienteAgregado = IMSSOFFLIN6_A3PacienteAgregado[0] ;
         A2PacienteNSS = IMSSOFFLIN6_A2PacienteNSS[0] ;
         A133PacienteNSSAgregado = IMSSOFFLIN6_A133PacienteNSSAgregado[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A88Cama));
         gxsyncline.add(A89DiagnosticoCirugia);
         gxsyncline.add(GXutil.timeToCharREST( A90DiagnosticoCirugiaFecha));
         gxsyncline.add(A86DiagnosticoComplemento);
         gxsyncline.add(GXutil.timeToCharREST( A103DiagnosticoFechaAlta));
         gxsyncline.add(GXutil.dateToCharREST( A85DiagnosticoFechaIngreso));
         gxsyncline.add(A87DiagnosticoResumen);
         gxsyncline.add(GXutil.rtrim( A93JSApMat));
         gxsyncline.add(GXutil.rtrim( A92JSApPat));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A94JSMatricula, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A91JSNombre));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A101MApMat, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A100MApPat, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A97MBApMat));
         gxsyncline.add(GXutil.rtrim( A96MBApPat));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A98MBMatricula, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A95MBNombre));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A102MMatricula, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A99MNombre, (byte)(4), (byte)(0), ".", "")));
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
      /* Using cursor IMSSOFFLIN7 */
      pr_default.execute(5);
      while ( (pr_default.getStatus(5) != 101) )
      {
         A314nada = IMSSOFFLIN7_A314nada[0] ;
         A302TextoDescripcion = IMSSOFFLIN7_A302TextoDescripcion[0] ;
         A301TextoTitulo = IMSSOFFLIN7_A301TextoTitulo[0] ;
         A67TextoId = IMSSOFFLIN7_A67TextoId[0] ;
         gxsyncline.add(A302TextoDescripcion);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A67TextoId, (byte)(4), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A67TextoId, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add(A301TextoTitulo);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A314nada, (byte)(4), (byte)(0), ".", "")));
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
                                           A133PacienteNSSAgregado ,
                                           AV3ColPacienteNSSAgregado },
                                           new int[] {
                                           TypeConstants.STRING, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN8 */
      pr_default.execute(6);
      while ( (pr_default.getStatus(6) != 101) )
      {
         A133PacienteNSSAgregado = IMSSOFFLIN8_A133PacienteNSSAgregado[0] ;
         A40000DXAuxImagenImg_GXI = IMSSOFFLIN8_A40000DXAuxImagenImg_GXI[0] ;
         A84DXAuxImagenUserAlta = IMSSOFFLIN8_A84DXAuxImagenUserAlta[0] ;
         A83DXAuxImagenFechaAlta = IMSSOFFLIN8_A83DXAuxImagenFechaAlta[0] ;
         A82DXAuxImagenImg = IMSSOFFLIN8_A82DXAuxImagenImg[0] ;
         A313DXAuxImagenExtension = IMSSOFFLIN8_A313DXAuxImagenExtension[0] ;
         A132DXAuxImagenNombre = IMSSOFFLIN8_A132DXAuxImagenNombre[0] ;
         A5DXAuxImagenId = IMSSOFFLIN8_A5DXAuxImagenId[0] ;
         A1CIE10Id = IMSSOFFLIN8_A1CIE10Id[0] ;
         A3PacienteAgregado = IMSSOFFLIN8_A3PacienteAgregado[0] ;
         A2PacienteNSS = IMSSOFFLIN8_A2PacienteNSS[0] ;
         A133PacienteNSSAgregado = IMSSOFFLIN8_A133PacienteNSSAgregado[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A313DXAuxImagenExtension));
         gxsyncline.add(GXutil.timeToCharREST( A83DXAuxImagenFechaAlta));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A5DXAuxImagenId, (byte)(4), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A5DXAuxImagenId, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add((!(GXutil.strcmp("", A40000DXAuxImagenImg_GXI)==0) ? GXutil.getRelativeBlobFile( A40000DXAuxImagenImg_GXI) : GXutil.rtrim( A82DXAuxImagenImg)));
         gxsyncline.add(A40000DXAuxImagenImg_GXI);
         gxsyncline.add(GXutil.rtrim( A132DXAuxImagenNombre));
         gxsyncline.add(GXutil.rtrim( A84DXAuxImagenUserAlta));
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
      gxsyncresponse_hash = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncresponse_hash.add(gxsyncheader);
      gxsyncline_hash = new com.genexus.internet.StringCollection() ;
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      pr_default.dynParam(7, new Object[]{ new Object[]{
                                           A133PacienteNSSAgregado ,
                                           AV3ColPacienteNSSAgregado },
                                           new int[] {
                                           TypeConstants.STRING, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN9 */
      pr_default.execute(7);
      while ( (pr_default.getStatus(7) != 101) )
      {
         A133PacienteNSSAgregado = IMSSOFFLIN9_A133PacienteNSSAgregado[0] ;
         A79DXAuxDoctoNombre = IMSSOFFLIN9_A79DXAuxDoctoNombre[0] ;
         A78DXAuxDoctoExtension = IMSSOFFLIN9_A78DXAuxDoctoExtension[0] ;
         A81DXAuxDoctoUserAlta = IMSSOFFLIN9_A81DXAuxDoctoUserAlta[0] ;
         A80DXAuxDoctoFechaAlta = IMSSOFFLIN9_A80DXAuxDoctoFechaAlta[0] ;
         A77DXAuxDoctoDocumento = IMSSOFFLIN9_A77DXAuxDoctoDocumento[0] ;
         A4DXAuxDoctoId = IMSSOFFLIN9_A4DXAuxDoctoId[0] ;
         A1CIE10Id = IMSSOFFLIN9_A1CIE10Id[0] ;
         A3PacienteAgregado = IMSSOFFLIN9_A3PacienteAgregado[0] ;
         A2PacienteNSS = IMSSOFFLIN9_A2PacienteNSS[0] ;
         A133PacienteNSSAgregado = IMSSOFFLIN9_A133PacienteNSSAgregado[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A1CIE10Id, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.getRelativeBlobFile( A77DXAuxDoctoDocumento));
         /* Blob file name not included in hash compute */
         gxsyncline.add(GXutil.rtrim( A78DXAuxDoctoExtension));
         gxsyncline_hash.add(GXutil.rtrim( A78DXAuxDoctoExtension));
         gxsyncline.add(GXutil.timeToCharREST( A80DXAuxDoctoFechaAlta));
         gxsyncline_hash.add(GXutil.timeToCharREST( A80DXAuxDoctoFechaAlta));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A4DXAuxDoctoId, (byte)(4), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A4DXAuxDoctoId, (byte)(4), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A4DXAuxDoctoId, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A79DXAuxDoctoNombre));
         gxsyncline_hash.add(GXutil.rtrim( A79DXAuxDoctoNombre));
         gxsyncline.add(GXutil.rtrim( A81DXAuxDoctoUserAlta));
         gxsyncline_hash.add(GXutil.rtrim( A81DXAuxDoctoUserAlta));
         gxsyncline.add(GXutil.rtrim( A3PacienteAgregado));
         gxsyncline_hash.add(GXutil.rtrim( A3PacienteAgregado));
         gxsynchashkey.add(GXutil.rtrim( A3PacienteAgregado));
         gxsyncline.add(GXutil.rtrim( A2PacienteNSS));
         gxsyncline_hash.add(GXutil.rtrim( A2PacienteNSS));
         gxsynchashkey.add(GXutil.rtrim( A2PacienteNSS));
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
                                           A133PacienteNSSAgregado ,
                                           AV3ColPacienteNSSAgregado },
                                           new int[] {
                                           TypeConstants.STRING, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN10 */
      pr_default.execute(8);
      while ( (pr_default.getStatus(8) != 101) )
      {
         A330ClavePresupuestal = IMSSOFFLIN10_A330ClavePresupuestal[0] ;
         A328IDEE = IMSSOFFLIN10_A328IDEE[0] ;
         n328IDEE = IMSSOFFLIN10_n328IDEE[0] ;
         A325CURP = IMSSOFFLIN10_A325CURP[0] ;
         n325CURP = IMSSOFFLIN10_n325CURP[0] ;
         A327DhUMF = IMSSOFFLIN10_A327DhUMF[0] ;
         n327DhUMF = IMSSOFFLIN10_n327DhUMF[0] ;
         A326DhDeleg = IMSSOFFLIN10_A326DhDeleg[0] ;
         n326DhDeleg = IMSSOFFLIN10_n326DhDeleg[0] ;
         A324Consultorio = IMSSOFFLIN10_A324Consultorio[0] ;
         n324Consultorio = IMSSOFFLIN10_n324Consultorio[0] ;
         A323ConDerechoSm = IMSSOFFLIN10_A323ConDerechoSm[0] ;
         n323ConDerechoSm = IMSSOFFLIN10_n323ConDerechoSm[0] ;
         A322ConDerechoInc = IMSSOFFLIN10_A322ConDerechoInc[0] ;
         n322ConDerechoInc = IMSSOFFLIN10_n322ConDerechoInc[0] ;
         A312PacienteServicioId = IMSSOFFLIN10_A312PacienteServicioId[0] ;
         A130PacienteCie10Id = IMSSOFFLIN10_A130PacienteCie10Id[0] ;
         A133PacienteNSSAgregado = IMSSOFFLIN10_A133PacienteNSSAgregado[0] ;
         A131PacienteCama = IMSSOFFLIN10_A131PacienteCama[0] ;
         A287PacienteDiagnosticoPhone = IMSSOFFLIN10_A287PacienteDiagnosticoPhone[0] ;
         A129PacienteDiagnosticoResumido = IMSSOFFLIN10_A129PacienteDiagnosticoResumido[0] ;
         A128PacienteDiagnostico = IMSSOFFLIN10_A128PacienteDiagnostico[0] ;
         A134PAcienteFechaIngreso = IMSSOFFLIN10_A134PAcienteFechaIngreso[0] ;
         A124PacienteNombreCompleto = IMSSOFFLIN10_A124PacienteNombreCompleto[0] ;
         A123PacienteReferencia = IMSSOFFLIN10_A123PacienteReferencia[0] ;
         n123PacienteReferencia = IMSSOFFLIN10_n123PacienteReferencia[0] ;
         A122PacienteFamiliar = IMSSOFFLIN10_A122PacienteFamiliar[0] ;
         n122PacienteFamiliar = IMSSOFFLIN10_n122PacienteFamiliar[0] ;
         A121PacienteTelefono = IMSSOFFLIN10_A121PacienteTelefono[0] ;
         n121PacienteTelefono = IMSSOFFLIN10_n121PacienteTelefono[0] ;
         A120PacienteGenero = IMSSOFFLIN10_A120PacienteGenero[0] ;
         n120PacienteGenero = IMSSOFFLIN10_n120PacienteGenero[0] ;
         A118PacienteEdad = IMSSOFFLIN10_A118PacienteEdad[0] ;
         A119PacienteFechaNacimiento = IMSSOFFLIN10_A119PacienteFechaNacimiento[0] ;
         A114PacienteApMat = IMSSOFFLIN10_A114PacienteApMat[0] ;
         n114PacienteApMat = IMSSOFFLIN10_n114PacienteApMat[0] ;
         A113PacienteApPat = IMSSOFFLIN10_A113PacienteApPat[0] ;
         A112PacienteNombre = IMSSOFFLIN10_A112PacienteNombre[0] ;
         A3PacienteAgregado = IMSSOFFLIN10_A3PacienteAgregado[0] ;
         A2PacienteNSS = IMSSOFFLIN10_A2PacienteNSS[0] ;
         gxsyncline.add(GXutil.rtrim( A325CURP));
         gxsyncline.add(GXutil.rtrim( A330ClavePresupuestal));
         gxsyncline.add(GXutil.rtrim( A322ConDerechoInc));
         gxsyncline.add(GXutil.rtrim( A323ConDerechoSm));
         gxsyncline.add(GXutil.rtrim( A324Consultorio));
         gxsyncline.add(GXutil.rtrim( A326DhDeleg));
         gxsyncline.add(GXutil.rtrim( A327DhUMF));
         gxsyncline.add(GXutil.rtrim( A328IDEE));
         gxsyncline.add(GXutil.dateToCharREST( A134PAcienteFechaIngreso));
         gxsyncline.add(GXutil.rtrim( A3PacienteAgregado));
         gxsynchashkey.add(GXutil.rtrim( A3PacienteAgregado));
         gxsyncline.add(GXutil.rtrim( A114PacienteApMat));
         gxsyncline.add(GXutil.rtrim( A113PacienteApPat));
         gxsyncline.add(GXutil.rtrim( A131PacienteCama));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A130PacienteCie10Id, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(A128PacienteDiagnostico);
         gxsyncline.add(A287PacienteDiagnosticoPhone);
         gxsyncline.add(A129PacienteDiagnosticoResumido);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A118PacienteEdad, (byte)(3), (byte)(0), ".", "")));
         gxsyncline.add(A122PacienteFamiliar);
         gxsyncline.add(GXutil.dateToCharREST( A119PacienteFechaNacimiento));
         gxsyncline.add(GXutil.rtrim( A120PacienteGenero));
         gxsyncline.add(GXutil.rtrim( A2PacienteNSS));
         gxsynchashkey.add(GXutil.rtrim( A2PacienteNSS));
         gxsyncline.add(A133PacienteNSSAgregado);
         gxsyncline.add(GXutil.rtrim( A112PacienteNombre));
         gxsyncline.add(GXutil.rtrim( A124PacienteNombreCompleto));
         gxsyncline.add(GXutil.rtrim( A123PacienteReferencia));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A312PacienteServicioId, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A121PacienteTelefono));
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
      /* Using cursor IMSSOFFLIN11 */
      pr_default.execute(9);
      while ( (pr_default.getStatus(9) != 101) )
      {
         A297ExtensionNombre = IMSSOFFLIN11_A297ExtensionNombre[0] ;
         A296ExtensionTipo = IMSSOFFLIN11_A296ExtensionTipo[0] ;
         A66ExtensionId = IMSSOFFLIN11_A66ExtensionId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A66ExtensionId, (byte)(4), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A66ExtensionId, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A297ExtensionNombre));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A296ExtensionTipo, (byte)(4), (byte)(0), ".", "")));
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
                                           new Long(A9DFFormInstId) ,
                                           AV2ColDFFormInstId },
                                           new int[] {
                                           TypeConstants.LONG, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN12 */
      pr_default.execute(10);
      while ( (pr_default.getStatus(10) != 101) )
      {
         A136FormatoPacienteMedicoMatricula = IMSSOFFLIN12_A136FormatoPacienteMedicoMatricula[0] ;
         A137FormatoPacienteMedicoNombre = IMSSOFFLIN12_A137FormatoPacienteMedicoNombre[0] ;
         A9DFFormInstId = IMSSOFFLIN12_A9DFFormInstId[0] ;
         A63FormatoPacienteAgregado = IMSSOFFLIN12_A63FormatoPacienteAgregado[0] ;
         A62FormatoPacienteNSS = IMSSOFFLIN12_A62FormatoPacienteNSS[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A9DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A9DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A63FormatoPacienteAgregado));
         gxsynchashkey.add(GXutil.rtrim( A63FormatoPacienteAgregado));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A136FormatoPacienteMedicoMatricula, (byte)(10), (byte)(0), ".", "")));
         gxsyncline.add(A137FormatoPacienteMedicoNombre);
         gxsyncline.add(GXutil.rtrim( A62FormatoPacienteNSS));
         gxsynchashkey.add(GXutil.rtrim( A62FormatoPacienteNSS));
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
      /* Using cursor IMSSOFFLIN13 */
      pr_default.execute(11);
      while ( (pr_default.getStatus(11) != 101) )
      {
         A304DFElemFormReq = IMSSOFFLIN13_A304DFElemFormReq[0] ;
         A299DFElemFormLoadRule = IMSSOFFLIN13_A299DFElemFormLoadRule[0] ;
         n299DFElemFormLoadRule = IMSSOFFLIN13_n299DFElemFormLoadRule[0] ;
         A263DFElemFormMetadata = IMSSOFFLIN13_A263DFElemFormMetadata[0] ;
         n263DFElemFormMetadata = IMSSOFFLIN13_n263DFElemFormMetadata[0] ;
         A264DFElemFormShwNbr = IMSSOFFLIN13_A264DFElemFormShwNbr[0] ;
         n264DFElemFormShwNbr = IMSSOFFLIN13_n264DFElemFormShwNbr[0] ;
         A262DFElemFormDateSel = IMSSOFFLIN13_A262DFElemFormDateSel[0] ;
         n262DFElemFormDateSel = IMSSOFFLIN13_n262DFElemFormDateSel[0] ;
         A259DFElemFormHasPmpt = IMSSOFFLIN13_A259DFElemFormHasPmpt[0] ;
         n259DFElemFormHasPmpt = IMSSOFFLIN13_n259DFElemFormHasPmpt[0] ;
         A184DFElemFormIsFlt = IMSSOFFLIN13_A184DFElemFormIsFlt[0] ;
         n184DFElemFormIsFlt = IMSSOFFLIN13_n184DFElemFormIsFlt[0] ;
         A183DFElemFormCmpWth = IMSSOFFLIN13_A183DFElemFormCmpWth[0] ;
         n183DFElemFormCmpWth = IMSSOFFLIN13_n183DFElemFormCmpWth[0] ;
         A182DFElemFormLblWth = IMSSOFFLIN13_A182DFElemFormLblWth[0] ;
         n182DFElemFormLblWth = IMSSOFFLIN13_n182DFElemFormLblWth[0] ;
         A307DFElemFormPrtPic = IMSSOFFLIN13_A307DFElemFormPrtPic[0] ;
         A282DFElemFormPrtShwNbr = IMSSOFFLIN13_A282DFElemFormPrtShwNbr[0] ;
         A281DFElemFormPrtNumColSkip = IMSSOFFLIN13_A281DFElemFormPrtNumColSkip[0] ;
         A273DFElemFormPrtNumRowSkip = IMSSOFFLIN13_A273DFElemFormPrtNumRowSkip[0] ;
         A271DFElemFormPrtAddRows = IMSSOFFLIN13_A271DFElemFormPrtAddRows[0] ;
         A270DFElemFormPrtName = IMSSOFFLIN13_A270DFElemFormPrtName[0] ;
         A191DFElemFormIsVisPrt = IMSSOFFLIN13_A191DFElemFormIsVisPrt[0] ;
         A190DFElemFormIsVis = IMSSOFFLIN13_A190DFElemFormIsVis[0] ;
         A189DFElemFormIsColap = IMSSOFFLIN13_A189DFElemFormIsColap[0] ;
         A188DFElemFormAllowIns = IMSSOFFLIN13_A188DFElemFormAllowIns[0] ;
         n188DFElemFormAllowIns = IMSSOFFLIN13_n188DFElemFormAllowIns[0] ;
         A187DFElemFormAllowUpd = IMSSOFFLIN13_A187DFElemFormAllowUpd[0] ;
         n187DFElemFormAllowUpd = IMSSOFFLIN13_n187DFElemFormAllowUpd[0] ;
         A186DFElemFormAllowDlt = IMSSOFFLIN13_A186DFElemFormAllowDlt[0] ;
         n186DFElemFormAllowDlt = IMSSOFFLIN13_n186DFElemFormAllowDlt[0] ;
         A181DFElemFormInhType = IMSSOFFLIN13_A181DFElemFormInhType[0] ;
         A36DFElemFormPos = IMSSOFFLIN13_A36DFElemFormPos[0] ;
         A185DFElemFormName = IMSSOFFLIN13_A185DFElemFormName[0] ;
         A19DFElemVer = IMSSOFFLIN13_A19DFElemVer[0] ;
         A18DFElemId = IMSSOFFLIN13_A18DFElemId[0] ;
         A12DFFormVer = IMSSOFFLIN13_A12DFFormVer[0] ;
         A11DFFormId = IMSSOFFLIN13_A11DFFormId[0] ;
         gxsyncline.add(GXutil.booltostr( A186DFElemFormAllowDlt));
         gxsyncline.add(GXutil.booltostr( A188DFElemFormAllowIns));
         gxsyncline.add(GXutil.booltostr( A187DFElemFormAllowUpd));
         gxsyncline.add(GXutil.rtrim( A183DFElemFormCmpWth));
         gxsyncline.add(GXutil.booltostr( A262DFElemFormDateSel));
         gxsyncline.add(GXutil.booltostr( A259DFElemFormHasPmpt));
         gxsyncline.add(GXutil.rtrim( A181DFElemFormInhType));
         gxsyncline.add(GXutil.booltostr( A189DFElemFormIsColap));
         gxsyncline.add(GXutil.rtrim( A184DFElemFormIsFlt));
         gxsyncline.add(GXutil.booltostr( A190DFElemFormIsVis));
         gxsyncline.add(GXutil.booltostr( A191DFElemFormIsVisPrt));
         gxsyncline.add(GXutil.rtrim( A182DFElemFormLblWth));
         gxsyncline.add(A299DFElemFormLoadRule);
         gxsyncline.add(A263DFElemFormMetadata);
         gxsyncline.add(GXutil.rtrim( A185DFElemFormName));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A36DFElemFormPos, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.booltostr( A271DFElemFormPrtAddRows));
         gxsyncline.add(GXutil.rtrim( A270DFElemFormPrtName));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A281DFElemFormPrtNumColSkip, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A273DFElemFormPrtNumRowSkip, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(A307DFElemFormPrtPic);
         gxsyncline.add(GXutil.booltostr( A282DFElemFormPrtShwNbr));
         gxsyncline.add(GXutil.booltostr( A304DFElemFormReq));
         gxsyncline.add(GXutil.booltostr( A264DFElemFormShwNbr));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A18DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A18DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A19DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A19DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A11DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A11DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A12DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A12DFFormVer, (byte)(6), (byte)(0), ".", "")));
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
      gxsyncresponse_hash = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncresponse_hash.add(gxsyncheader);
      gxsyncline_hash = new com.genexus.internet.StringCollection() ;
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      pr_default.dynParam(12, new Object[]{ new Object[]{
                                           new Long(A9DFFormInstId) ,
                                           AV2ColDFFormInstId },
                                           new int[] {
                                           TypeConstants.LONG, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN14 */
      pr_default.execute(12);
      while ( (pr_default.getStatus(12) != 101) )
      {
         A145DFElemFormInstFileName = IMSSOFFLIN14_A145DFElemFormInstFileName[0] ;
         n145DFElemFormInstFileName = IMSSOFFLIN14_n145DFElemFormInstFileName[0] ;
         A144DFElemFormInstFileType = IMSSOFFLIN14_A144DFElemFormInstFileType[0] ;
         n144DFElemFormInstFileType = IMSSOFFLIN14_n144DFElemFormInstFileType[0] ;
         A143DFElemFormInstBlob = IMSSOFFLIN14_A143DFElemFormInstBlob[0] ;
         n143DFElemFormInstBlob = IMSSOFFLIN14_n143DFElemFormInstBlob[0] ;
         A141DFElemFormInstVal = IMSSOFFLIN14_A141DFElemFormInstVal[0] ;
         n141DFElemFormInstVal = IMSSOFFLIN14_n141DFElemFormInstVal[0] ;
         A19DFElemVer = IMSSOFFLIN14_A19DFElemVer[0] ;
         A18DFElemId = IMSSOFFLIN14_A18DFElemId[0] ;
         A9DFFormInstId = IMSSOFFLIN14_A9DFFormInstId[0] ;
         gxsyncline.add(GXutil.getRelativeBlobFile( A143DFElemFormInstBlob));
         /* Blob file name not included in hash compute */
         gxsyncline.add(GXutil.rtrim( A145DFElemFormInstFileName));
         gxsyncline_hash.add(GXutil.rtrim( A145DFElemFormInstFileName));
         gxsyncline.add(GXutil.rtrim( A144DFElemFormInstFileType));
         gxsyncline_hash.add(GXutil.rtrim( A144DFElemFormInstFileType));
         gxsyncline.add(A141DFElemFormInstVal);
         gxsyncline_hash.add(A141DFElemFormInstVal);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A18DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A18DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A18DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A19DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A19DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A19DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A9DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A9DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A9DFFormInstId, (byte)(10), (byte)(0), ".", "")));
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
         pr_default.readNext(12);
      }
      pr_default.close(12);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
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
      gxsyncresponse_hash = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncresponse_hash.add(gxsyncheader);
      gxsyncline_hash = new com.genexus.internet.StringCollection() ;
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      pr_default.dynParam(13, new Object[]{ new Object[]{
                                           new Long(A9DFFormInstId) ,
                                           AV2ColDFFormInstId },
                                           new int[] {
                                           TypeConstants.LONG, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN15 */
      pr_default.execute(13);
      while ( (pr_default.getStatus(13) != 101) )
      {
         A148DFElemFormInstSubElemFileName = IMSSOFFLIN15_A148DFElemFormInstSubElemFileName[0] ;
         n148DFElemFormInstSubElemFileName = IMSSOFFLIN15_n148DFElemFormInstSubElemFileName[0] ;
         A147DFElemFormInstSubElemFileType = IMSSOFFLIN15_A147DFElemFormInstSubElemFileType[0] ;
         n147DFElemFormInstSubElemFileType = IMSSOFFLIN15_n147DFElemFormInstSubElemFileType[0] ;
         A37DFSubElemFormElemId = IMSSOFFLIN15_A37DFSubElemFormElemId[0] ;
         A38DFSubElemFormElemVer = IMSSOFFLIN15_A38DFSubElemFormElemVer[0] ;
         A69DFElemFormInstSubElemRow = IMSSOFFLIN15_A69DFElemFormInstSubElemRow[0] ;
         A142DFElemFormInstSubElemVal = IMSSOFFLIN15_A142DFElemFormInstSubElemVal[0] ;
         n142DFElemFormInstSubElemVal = IMSSOFFLIN15_n142DFElemFormInstSubElemVal[0] ;
         A146DFElemFormInstSubElemBlob = IMSSOFFLIN15_A146DFElemFormInstSubElemBlob[0] ;
         n146DFElemFormInstSubElemBlob = IMSSOFFLIN15_n146DFElemFormInstSubElemBlob[0] ;
         A68DFElemFormInstSubElemId = IMSSOFFLIN15_A68DFElemFormInstSubElemId[0] ;
         A19DFElemVer = IMSSOFFLIN15_A19DFElemVer[0] ;
         A18DFElemId = IMSSOFFLIN15_A18DFElemId[0] ;
         A9DFFormInstId = IMSSOFFLIN15_A9DFFormInstId[0] ;
         gxsyncline.add(GXutil.getRelativeBlobFile( A146DFElemFormInstSubElemBlob));
         /* Blob file name not included in hash compute */
         gxsyncline.add(GXutil.rtrim( A148DFElemFormInstSubElemFileName));
         gxsyncline_hash.add(GXutil.rtrim( A148DFElemFormInstSubElemFileName));
         gxsyncline.add(GXutil.rtrim( A147DFElemFormInstSubElemFileType));
         gxsyncline_hash.add(GXutil.rtrim( A147DFElemFormInstSubElemFileType));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A68DFElemFormInstSubElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A68DFElemFormInstSubElemId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A68DFElemFormInstSubElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A69DFElemFormInstSubElemRow, (byte)(6), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A69DFElemFormInstSubElemRow, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(A142DFElemFormInstSubElemVal);
         gxsyncline_hash.add(A142DFElemFormInstSubElemVal);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A18DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A18DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A18DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A19DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A19DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A19DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A9DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A9DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A9DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A37DFSubElemFormElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A37DFSubElemFormElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A38DFSubElemFormElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A38DFSubElemFormElemVer, (byte)(6), (byte)(0), ".", "")));
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
         pr_default.readNext(13);
      }
      pr_default.close(13);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
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
      gxsyncresponse_hash = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncresponse_hash.add(gxsyncheader);
      gxsyncline_hash = new com.genexus.internet.StringCollection() ;
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN16 */
      pr_default.execute(14);
      while ( (pr_default.getStatus(14) != 101) )
      {
         A284DFTempOutFm = IMSSOFFLIN16_A284DFTempOutFm[0] ;
         A278DFTempAddParmPrgName = IMSSOFFLIN16_A278DFTempAddParmPrgName[0] ;
         A277DFTempBlob = IMSSOFFLIN16_A277DFTempBlob[0] ;
         A286DFTempFm = IMSSOFFLIN16_A286DFTempFm[0] ;
         A283DFTempDsc = IMSSOFFLIN16_A283DFTempDsc[0] ;
         A55DFTempName = IMSSOFFLIN16_A55DFTempName[0] ;
         A12DFFormVer = IMSSOFFLIN16_A12DFFormVer[0] ;
         A11DFFormId = IMSSOFFLIN16_A11DFFormId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A11DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A11DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A11DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A12DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A12DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A12DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(A278DFTempAddParmPrgName);
         gxsyncline_hash.add(A278DFTempAddParmPrgName);
         gxsyncline.add(GXutil.getRelativeBlobFile( A277DFTempBlob));
         /* Blob file name not included in hash compute */
         gxsyncline.add(A283DFTempDsc);
         gxsyncline_hash.add(A283DFTempDsc);
         gxsyncline.add(GXutil.rtrim( A286DFTempFm));
         gxsyncline_hash.add(GXutil.rtrim( A286DFTempFm));
         gxsyncline.add(GXutil.rtrim( A55DFTempName));
         gxsyncline_hash.add(GXutil.rtrim( A55DFTempName));
         gxsynchashkey.add(GXutil.rtrim( A55DFTempName));
         gxsyncline.add(GXutil.rtrim( A284DFTempOutFm));
         gxsyncline_hash.add(GXutil.rtrim( A284DFTempOutFm));
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
         pr_default.readNext(14);
      }
      pr_default.close(14);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
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
      /* Using cursor IMSSOFFLIN17 */
      pr_default.execute(15);
      while ( (pr_default.getStatus(15) != 101) )
      {
         A298DFFormIsSD = IMSSOFFLIN17_A298DFFormIsSD[0] ;
         A157DFFormRunDLT = IMSSOFFLIN17_A157DFFormRunDLT[0] ;
         A233DFFormHelpURL = IMSSOFFLIN17_A233DFFormHelpURL[0] ;
         A173DFFormPrefix = IMSSOFFLIN17_A173DFFormPrefix[0] ;
         A232DFFormPmtHgh = IMSSOFFLIN17_A232DFFormPmtHgh[0] ;
         n232DFFormPmtHgh = IMSSOFFLIN17_n232DFFormPmtHgh[0] ;
         A231DFFormPmtWth = IMSSOFFLIN17_A231DFFormPmtWth[0] ;
         n231DFFormPmtWth = IMSSOFFLIN17_n231DFFormPmtWth[0] ;
         A234DFFormAct = IMSSOFFLIN17_A234DFFormAct[0] ;
         A308DFFormDsc = IMSSOFFLIN17_A308DFFormDsc[0] ;
         A31DFFormName = IMSSOFFLIN17_A31DFFormName[0] ;
         A30DFFormGuid = IMSSOFFLIN17_A30DFFormGuid[0] ;
         A12DFFormVer = IMSSOFFLIN17_A12DFFormVer[0] ;
         A11DFFormId = IMSSOFFLIN17_A11DFFormId[0] ;
         gxsyncline.add(GXutil.booltostr( A234DFFormAct));
         gxsyncline.add(A308DFFormDsc);
         gxsyncline.add(A30DFFormGuid.toString());
         gxsyncline.add(A233DFFormHelpURL);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A11DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A11DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.booltostr( A298DFFormIsSD));
         gxsyncline.add(GXutil.rtrim( A31DFFormName));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A232DFFormPmtHgh, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A231DFFormPmtWth, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(A173DFFormPrefix);
         gxsyncline.add(GXutil.booltostr( A157DFFormRunDLT));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A12DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A12DFFormVer, (byte)(6), (byte)(0), ".", "")));
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
         pr_default.readNext(15);
      }
      pr_default.close(15);
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
         A222DFDomStaValOptDsc = IMSSOFFLIN18_A222DFDomStaValOptDsc[0] ;
         A34DFDomStaValOptOrd = IMSSOFFLIN18_A34DFDomStaValOptOrd[0] ;
         A33DFDomStaValOptCod = IMSSOFFLIN18_A33DFDomStaValOptCod[0] ;
         A32DFDomId = IMSSOFFLIN18_A32DFDomId[0] ;
         n32DFDomId = IMSSOFFLIN18_n32DFDomId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A32DFDomId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A32DFDomId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A33DFDomStaValOptCod));
         gxsynchashkey.add(GXutil.rtrim( A33DFDomStaValOptCod));
         gxsyncline.add(GXutil.rtrim( A222DFDomStaValOptDsc));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A34DFDomStaValOptOrd, (byte)(6), (byte)(0), ".", "")));
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
      gxsyncresponse_hash = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncresponse_hash.add(gxsyncheader);
      gxsyncline_hash = new com.genexus.internet.StringCollection() ;
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      pr_default.dynParam(17, new Object[]{ new Object[]{
                                           new Long(A9DFFormInstId) ,
                                           AV2ColDFFormInstId },
                                           new int[] {
                                           TypeConstants.LONG, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN19 */
      pr_default.execute(17);
      while ( (pr_default.getStatus(17) != 101) )
      {
         A197DFFormInstSignedPDF = IMSSOFFLIN19_A197DFFormInstSignedPDF[0] ;
         n197DFFormInstSignedPDF = IMSSOFFLIN19_n197DFFormInstSignedPDF[0] ;
         A198DFFormInstSignedBy = IMSSOFFLIN19_A198DFFormInstSignedBy[0] ;
         n198DFFormInstSignedBy = IMSSOFFLIN19_n198DFFormInstSignedBy[0] ;
         A155DFFormInstDT = IMSSOFFLIN19_A155DFFormInstDT[0] ;
         A29DFFormInstFormVer = IMSSOFFLIN19_A29DFFormInstFormVer[0] ;
         A28DFFormInstFormId = IMSSOFFLIN19_A28DFFormInstFormId[0] ;
         A9DFFormInstId = IMSSOFFLIN19_A9DFFormInstId[0] ;
         gxsyncline.add(GXutil.timeToCharREST( A155DFFormInstDT));
         gxsyncline_hash.add(GXutil.timeToCharREST( A155DFFormInstDT));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A28DFFormInstFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A28DFFormInstFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A29DFFormInstFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A29DFFormInstFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A9DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A9DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A9DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsyncline.add(A198DFFormInstSignedBy);
         gxsyncline_hash.add(A198DFFormInstSignedBy);
         gxsyncline.add(GXutil.getRelativeBlobFile( A197DFFormInstSignedPDF));
         /* Blob file name not included in hash compute */
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
         pr_default.readNext(17);
      }
      pr_default.close(17);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
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
         A305DFElemReq = IMSSOFFLIN20_A305DFElemReq[0] ;
         A300DFElemLoadRule = IMSSOFFLIN20_A300DFElemLoadRule[0] ;
         n300DFElemLoadRule = IMSSOFFLIN20_n300DFElemLoadRule[0] ;
         A265DFElemMetadata = IMSSOFFLIN20_A265DFElemMetadata[0] ;
         n265DFElemMetadata = IMSSOFFLIN20_n265DFElemMetadata[0] ;
         A238DFElemIsColap = IMSSOFFLIN20_A238DFElemIsColap[0] ;
         A306DFElemPrtPic = IMSSOFFLIN20_A306DFElemPrtPic[0] ;
         A280DFElemPrtShwNbr = IMSSOFFLIN20_A280DFElemPrtShwNbr[0] ;
         A279DFElemPrtNumColSkip = IMSSOFFLIN20_A279DFElemPrtNumColSkip[0] ;
         A274DFElemPrtNumRowSkip = IMSSOFFLIN20_A274DFElemPrtNumRowSkip[0] ;
         A272DFElemPrtAddRows = IMSSOFFLIN20_A272DFElemPrtAddRows[0] ;
         A269DFElemPrtName = IMSSOFFLIN20_A269DFElemPrtName[0] ;
         A260DFElemIsVisPrt = IMSSOFFLIN20_A260DFElemIsVisPrt[0] ;
         A237DFElemIsVis = IMSSOFFLIN20_A237DFElemIsVis[0] ;
         A257DFElemLblWth = IMSSOFFLIN20_A257DFElemLblWth[0] ;
         n257DFElemLblWth = IMSSOFFLIN20_n257DFElemLblWth[0] ;
         A243DFElemCmpWth = IMSSOFFLIN20_A243DFElemCmpWth[0] ;
         n243DFElemCmpWth = IMSSOFFLIN20_n243DFElemCmpWth[0] ;
         A242DFElemIsFlt = IMSSOFFLIN20_A242DFElemIsFlt[0] ;
         n242DFElemIsFlt = IMSSOFFLIN20_n242DFElemIsFlt[0] ;
         A256DFElemFileType = IMSSOFFLIN20_A256DFElemFileType[0] ;
         n256DFElemFileType = IMSSOFFLIN20_n256DFElemFileType[0] ;
         A254DFElemRegexVal = IMSSOFFLIN20_A254DFElemRegexVal[0] ;
         n254DFElemRegexVal = IMSSOFFLIN20_n254DFElemRegexVal[0] ;
         A253DFElemAllowDlt = IMSSOFFLIN20_A253DFElemAllowDlt[0] ;
         n253DFElemAllowDlt = IMSSOFFLIN20_n253DFElemAllowDlt[0] ;
         A252DFElemAllowUpd = IMSSOFFLIN20_A252DFElemAllowUpd[0] ;
         n252DFElemAllowUpd = IMSSOFFLIN20_n252DFElemAllowUpd[0] ;
         A251DFElemAllowIns = IMSSOFFLIN20_A251DFElemAllowIns[0] ;
         n251DFElemAllowIns = IMSSOFFLIN20_n251DFElemAllowIns[0] ;
         A250DFElemUseBtns = IMSSOFFLIN20_A250DFElemUseBtns[0] ;
         n250DFElemUseBtns = IMSSOFFLIN20_n250DFElemUseBtns[0] ;
         A249DFElemIsOrd = IMSSOFFLIN20_A249DFElemIsOrd[0] ;
         n249DFElemIsOrd = IMSSOFFLIN20_n249DFElemIsOrd[0] ;
         A248DFElemMaxSuggRes = IMSSOFFLIN20_A248DFElemMaxSuggRes[0] ;
         n248DFElemMaxSuggRes = IMSSOFFLIN20_n248DFElemMaxSuggRes[0] ;
         A247DFElemForceSuggSel = IMSSOFFLIN20_A247DFElemForceSuggSel[0] ;
         n247DFElemForceSuggSel = IMSSOFFLIN20_n247DFElemForceSuggSel[0] ;
         A246DFElemMinCntCharSugg = IMSSOFFLIN20_A246DFElemMinCntCharSugg[0] ;
         n246DFElemMinCntCharSugg = IMSSOFFLIN20_n246DFElemMinCntCharSugg[0] ;
         A258DFElemDscPrgName = IMSSOFFLIN20_A258DFElemDscPrgName[0] ;
         A245DFElemLoadPrgName = IMSSOFFLIN20_A245DFElemLoadPrgName[0] ;
         n245DFElemLoadPrgName = IMSSOFFLIN20_n245DFElemLoadPrgName[0] ;
         A267DFElemBtnPos = IMSSOFFLIN20_A267DFElemBtnPos[0] ;
         n267DFElemBtnPos = IMSSOFFLIN20_n267DFElemBtnPos[0] ;
         A268DFElemShwNbrLbl = IMSSOFFLIN20_A268DFElemShwNbrLbl[0] ;
         n268DFElemShwNbrLbl = IMSSOFFLIN20_n268DFElemShwNbrLbl[0] ;
         A266DFElemShwNbr = IMSSOFFLIN20_A266DFElemShwNbr[0] ;
         n266DFElemShwNbr = IMSSOFFLIN20_n266DFElemShwNbr[0] ;
         A261DFElemDateSel = IMSSOFFLIN20_A261DFElemDateSel[0] ;
         n261DFElemDateSel = IMSSOFFLIN20_n261DFElemDateSel[0] ;
         A244DFElemHasPmpt = IMSSOFFLIN20_A244DFElemHasPmpt[0] ;
         n244DFElemHasPmpt = IMSSOFFLIN20_n244DFElemHasPmpt[0] ;
         A180DFElemDftVal = IMSSOFFLIN20_A180DFElemDftVal[0] ;
         n180DFElemDftVal = IMSSOFFLIN20_n180DFElemDftVal[0] ;
         A241DFElemCntCols = IMSSOFFLIN20_A241DFElemCntCols[0] ;
         n241DFElemCntCols = IMSSOFFLIN20_n241DFElemCntCols[0] ;
         A240DFElemCntRows = IMSSOFFLIN20_A240DFElemCntRows[0] ;
         n240DFElemCntRows = IMSSOFFLIN20_n240DFElemCntRows[0] ;
         A239DFElemCntDec = IMSSOFFLIN20_A239DFElemCntDec[0] ;
         n239DFElemCntDec = IMSSOFFLIN20_n239DFElemCntDec[0] ;
         A255DFElemWth = IMSSOFFLIN20_A255DFElemWth[0] ;
         n255DFElemWth = IMSSOFFLIN20_n255DFElemWth[0] ;
         A236DFElemLen = IMSSOFFLIN20_A236DFElemLen[0] ;
         n236DFElemLen = IMSSOFFLIN20_n236DFElemLen[0] ;
         A196DFElemDsp = IMSSOFFLIN20_A196DFElemDsp[0] ;
         n196DFElemDsp = IMSSOFFLIN20_n196DFElemDsp[0] ;
         A178DFElemType = IMSSOFFLIN20_A178DFElemType[0] ;
         A32DFDomId = IMSSOFFLIN20_A32DFDomId[0] ;
         n32DFDomId = IMSSOFFLIN20_n32DFDomId[0] ;
         A192DFElemClsName = IMSSOFFLIN20_A192DFElemClsName[0] ;
         n192DFElemClsName = IMSSOFFLIN20_n192DFElemClsName[0] ;
         A235DFElemDsc = IMSSOFFLIN20_A235DFElemDsc[0] ;
         n235DFElemDsc = IMSSOFFLIN20_n235DFElemDsc[0] ;
         A149DFElemName = IMSSOFFLIN20_A149DFElemName[0] ;
         A35DFElemGuid = IMSSOFFLIN20_A35DFElemGuid[0] ;
         A19DFElemVer = IMSSOFFLIN20_A19DFElemVer[0] ;
         A18DFElemId = IMSSOFFLIN20_A18DFElemId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A32DFDomId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.booltostr( A253DFElemAllowDlt));
         gxsyncline.add(GXutil.booltostr( A251DFElemAllowIns));
         gxsyncline.add(GXutil.booltostr( A252DFElemAllowUpd));
         gxsyncline.add(GXutil.rtrim( A267DFElemBtnPos));
         gxsyncline.add(GXutil.rtrim( A192DFElemClsName));
         gxsyncline.add(GXutil.rtrim( A243DFElemCmpWth));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A241DFElemCntCols, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A239DFElemCntDec, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A240DFElemCntRows, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.booltostr( A261DFElemDateSel));
         gxsyncline.add(GXutil.rtrim( A180DFElemDftVal));
         gxsyncline.add(A235DFElemDsc);
         gxsyncline.add(A258DFElemDscPrgName);
         gxsyncline.add(GXutil.rtrim( A196DFElemDsp));
         gxsyncline.add(GXutil.rtrim( A256DFElemFileType));
         gxsyncline.add(GXutil.booltostr( A247DFElemForceSuggSel));
         gxsyncline.add(A35DFElemGuid.toString());
         gxsyncline.add(GXutil.booltostr( A244DFElemHasPmpt));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A18DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A18DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.booltostr( A238DFElemIsColap));
         gxsyncline.add(GXutil.rtrim( A242DFElemIsFlt));
         gxsyncline.add(GXutil.booltostr( A249DFElemIsOrd));
         gxsyncline.add(GXutil.booltostr( A237DFElemIsVis));
         gxsyncline.add(GXutil.booltostr( A260DFElemIsVisPrt));
         gxsyncline.add(GXutil.rtrim( A257DFElemLblWth));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A236DFElemLen, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(A245DFElemLoadPrgName);
         gxsyncline.add(A300DFElemLoadRule);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A248DFElemMaxSuggRes, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(A265DFElemMetadata);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A246DFElemMinCntCharSugg, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A149DFElemName));
         gxsyncline.add(GXutil.booltostr( A272DFElemPrtAddRows));
         gxsyncline.add(GXutil.rtrim( A269DFElemPrtName));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A279DFElemPrtNumColSkip, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A274DFElemPrtNumRowSkip, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(A306DFElemPrtPic);
         gxsyncline.add(GXutil.booltostr( A280DFElemPrtShwNbr));
         gxsyncline.add(GXutil.rtrim( A254DFElemRegexVal));
         gxsyncline.add(GXutil.booltostr( A305DFElemReq));
         gxsyncline.add(GXutil.booltostr( A266DFElemShwNbr));
         gxsyncline.add(GXutil.rtrim( A268DFElemShwNbrLbl));
         gxsyncline.add(GXutil.rtrim( A178DFElemType));
         gxsyncline.add(GXutil.booltostr( A250DFElemUseBtns));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A19DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A19DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A255DFElemWth, (byte)(6), (byte)(0), ".", "")));
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

   /*  Synchronize for table (Full)  EspecialidadFormato */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtEspecialidadFormato( )
   {
      /* Begin Synchronize  EspecialidadFormato */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("EspecialidadFormato");
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
         A71cveEspecialidad = IMSSOFFLIN21_A71cveEspecialidad[0] ;
         A12DFFormVer = IMSSOFFLIN21_A12DFFormVer[0] ;
         A11DFFormId = IMSSOFFLIN21_A11DFFormId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A11DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A11DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A12DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A12DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A71cveEspecialidad));
         gxsynchashkey.add(GXutil.rtrim( A71cveEspecialidad));
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
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "EspecialidadFormato" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
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

   /*  Synchronize for table (Full)  PacienteDiagnostico */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtPacienteDiagnostico( )
   {
      /* Begin Synchronize  PacienteDiagnostico */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("PacienteDiagnostico");
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
         A348PXDXFechaAsignacion = IMSSOFFLIN22_A348PXDXFechaAsignacion[0] ;
         A347OcaSer = IMSSOFFLIN22_A347OcaSer[0] ;
         A346TpoDX = IMSSOFFLIN22_A346TpoDX[0] ;
         A345DX = IMSSOFFLIN22_A345DX[0] ;
         A353IDEEPaciente = IMSSOFFLIN22_A353IDEEPaciente[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A345DX, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A345DX, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A353IDEEPaciente));
         gxsynchashkey.add(GXutil.rtrim( A353IDEEPaciente));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A347OcaSer, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.timeToCharREST( A348PXDXFechaAsignacion));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A346TpoDX, (byte)(4), (byte)(0), ".", "")));
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
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "PacienteDiagnostico" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
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
         A310DFDomPrtDsc = IMSSOFFLIN23_A310DFDomPrtDsc[0] ;
         n310DFDomPrtDsc = IMSSOFFLIN23_n310DFDomPrtDsc[0] ;
         A223DFDomLblWth = IMSSOFFLIN23_A223DFDomLblWth[0] ;
         n223DFDomLblWth = IMSSOFFLIN23_n223DFDomLblWth[0] ;
         A219DFDomCmpWth = IMSSOFFLIN23_A219DFDomCmpWth[0] ;
         n219DFDomCmpWth = IMSSOFFLIN23_n219DFDomCmpWth[0] ;
         A218DFDomIsFlt = IMSSOFFLIN23_A218DFDomIsFlt[0] ;
         n218DFDomIsFlt = IMSSOFFLIN23_n218DFDomIsFlt[0] ;
         A221DFDomFileType = IMSSOFFLIN23_A221DFDomFileType[0] ;
         n221DFDomFileType = IMSSOFFLIN23_n221DFDomFileType[0] ;
         A217DFDomRegexVal = IMSSOFFLIN23_A217DFDomRegexVal[0] ;
         A213DFDomAllowDlt = IMSSOFFLIN23_A213DFDomAllowDlt[0] ;
         n213DFDomAllowDlt = IMSSOFFLIN23_n213DFDomAllowDlt[0] ;
         A212DFDomAllowUpd = IMSSOFFLIN23_A212DFDomAllowUpd[0] ;
         n212DFDomAllowUpd = IMSSOFFLIN23_n212DFDomAllowUpd[0] ;
         A211DFDomAllowIns = IMSSOFFLIN23_A211DFDomAllowIns[0] ;
         n211DFDomAllowIns = IMSSOFFLIN23_n211DFDomAllowIns[0] ;
         A210DFDomUseBtns = IMSSOFFLIN23_A210DFDomUseBtns[0] ;
         n210DFDomUseBtns = IMSSOFFLIN23_n210DFDomUseBtns[0] ;
         A209DFDomIsOrd = IMSSOFFLIN23_A209DFDomIsOrd[0] ;
         n209DFDomIsOrd = IMSSOFFLIN23_n209DFDomIsOrd[0] ;
         A207DFDomMaxSuggRes = IMSSOFFLIN23_A207DFDomMaxSuggRes[0] ;
         n207DFDomMaxSuggRes = IMSSOFFLIN23_n207DFDomMaxSuggRes[0] ;
         A206DFDomForceSuggSel = IMSSOFFLIN23_A206DFDomForceSuggSel[0] ;
         n206DFDomForceSuggSel = IMSSOFFLIN23_n206DFDomForceSuggSel[0] ;
         A205DFDomMinCntCharSugg = IMSSOFFLIN23_A205DFDomMinCntCharSugg[0] ;
         n205DFDomMinCntCharSugg = IMSSOFFLIN23_n205DFDomMinCntCharSugg[0] ;
         A208DFDomDftVal = IMSSOFFLIN23_A208DFDomDftVal[0] ;
         n208DFDomDftVal = IMSSOFFLIN23_n208DFDomDftVal[0] ;
         A216DFDomCntCols = IMSSOFFLIN23_A216DFDomCntCols[0] ;
         A215DFDomCntRows = IMSSOFFLIN23_A215DFDomCntRows[0] ;
         A214DFDomCntDec = IMSSOFFLIN23_A214DFDomCntDec[0] ;
         A220DFDomWth = IMSSOFFLIN23_A220DFDomWth[0] ;
         A204DFDomLen = IMSSOFFLIN23_A204DFDomLen[0] ;
         A195DFDomDsp = IMSSOFFLIN23_A195DFDomDsp[0] ;
         n195DFDomDsp = IMSSOFFLIN23_n195DFDomDsp[0] ;
         A194DFDomType = IMSSOFFLIN23_A194DFDomType[0] ;
         A224DFDomGUID = IMSSOFFLIN23_A224DFDomGUID[0] ;
         A203DFDomDsc = IMSSOFFLIN23_A203DFDomDsc[0] ;
         A32DFDomId = IMSSOFFLIN23_A32DFDomId[0] ;
         n32DFDomId = IMSSOFFLIN23_n32DFDomId[0] ;
         gxsyncline.add(GXutil.booltostr( A213DFDomAllowDlt));
         gxsyncline.add(GXutil.booltostr( A211DFDomAllowIns));
         gxsyncline.add(GXutil.booltostr( A212DFDomAllowUpd));
         gxsyncline.add(GXutil.rtrim( A219DFDomCmpWth));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A216DFDomCntCols, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A214DFDomCntDec, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A215DFDomCntRows, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A208DFDomDftVal));
         gxsyncline.add(GXutil.rtrim( A203DFDomDsc));
         gxsyncline.add(GXutil.rtrim( A195DFDomDsp));
         gxsyncline.add(GXutil.rtrim( A221DFDomFileType));
         gxsyncline.add(GXutil.booltostr( A206DFDomForceSuggSel));
         gxsyncline.add(A224DFDomGUID.toString());
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A32DFDomId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A32DFDomId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A218DFDomIsFlt));
         gxsyncline.add(GXutil.booltostr( A209DFDomIsOrd));
         gxsyncline.add(GXutil.rtrim( A223DFDomLblWth));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A204DFDomLen, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A207DFDomMaxSuggRes, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A205DFDomMinCntCharSugg, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.booltostr( A310DFDomPrtDsc));
         gxsyncline.add(GXutil.rtrim( A217DFDomRegexVal));
         gxsyncline.add(GXutil.rtrim( A194DFDomType));
         gxsyncline.add(GXutil.booltostr( A210DFDomUseBtns));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A220DFDomWth, (byte)(6), (byte)(0), ".", "")));
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
      /* Using cursor IMSSOFFLIN24 */
      pr_default.execute(22);
      while ( (pr_default.getStatus(22) != 101) )
      {
         A14DFFormRstVal = IMSSOFFLIN24_A14DFFormRstVal[0] ;
         A13DFFormRstId = IMSSOFFLIN24_A13DFFormRstId[0] ;
         A12DFFormVer = IMSSOFFLIN24_A12DFFormVer[0] ;
         A11DFFormId = IMSSOFFLIN24_A11DFFormId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A11DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A11DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A13DFFormRstId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A13DFFormRstId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A14DFFormRstVal));
         gxsynchashkey.add(GXutil.rtrim( A14DFFormRstVal));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A12DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A12DFFormVer, (byte)(6), (byte)(0), ".", "")));
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
      /* Using cursor IMSSOFFLIN25 */
      pr_default.execute(23);
      while ( (pr_default.getStatus(23) != 101) )
      {
         A164DFUserRstPwdIni = IMSSOFFLIN25_A164DFUserRstPwdIni[0] ;
         A24DFUserRstVal = IMSSOFFLIN25_A24DFUserRstVal[0] ;
         A23DFUserRstId = IMSSOFFLIN25_A23DFUserRstId[0] ;
         A22DFUserExtId = IMSSOFFLIN25_A22DFUserExtId[0] ;
         gxsyncline.add(A22DFUserExtId);
         gxsynchashkey.add(A22DFUserExtId);
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A23DFUserRstId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A23DFUserRstId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.booltostr( A164DFUserRstPwdIni));
         gxsyncline.add(GXutil.rtrim( A24DFUserRstVal));
         gxsynchashkey.add(GXutil.rtrim( A24DFUserRstVal));
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
      /* Using cursor IMSSOFFLIN26 */
      pr_default.execute(24);
      while ( (pr_default.getStatus(24) != 101) )
      {
         A39DFSubElemFormPos = IMSSOFFLIN26_A39DFSubElemFormPos[0] ;
         n39DFSubElemFormPos = IMSSOFFLIN26_n39DFSubElemFormPos[0] ;
         A38DFSubElemFormElemVer = IMSSOFFLIN26_A38DFSubElemFormElemVer[0] ;
         A37DFSubElemFormElemId = IMSSOFFLIN26_A37DFSubElemFormElemId[0] ;
         A19DFElemVer = IMSSOFFLIN26_A19DFElemVer[0] ;
         A18DFElemId = IMSSOFFLIN26_A18DFElemId[0] ;
         A12DFFormVer = IMSSOFFLIN26_A12DFFormVer[0] ;
         A11DFFormId = IMSSOFFLIN26_A11DFFormId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A18DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A18DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A19DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A19DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A11DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A11DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A12DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A12DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A37DFSubElemFormElemId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A37DFSubElemFormElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A38DFSubElemFormElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A38DFSubElemFormElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A39DFSubElemFormPos, (byte)(6), (byte)(0), ".", "")));
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
      /* Using cursor IMSSOFFLIN27 */
      pr_default.execute(25);
      while ( (pr_default.getStatus(25) != 101) )
      {
         A42DFFilElemFormElemVer = IMSSOFFLIN27_A42DFFilElemFormElemVer[0] ;
         A41DFFilElemFormElemId = IMSSOFFLIN27_A41DFFilElemFormElemId[0] ;
         A43DFFilElemFormPos = IMSSOFFLIN27_A43DFFilElemFormPos[0] ;
         A40DFFilElemFormId = IMSSOFFLIN27_A40DFFilElemFormId[0] ;
         A19DFElemVer = IMSSOFFLIN27_A19DFElemVer[0] ;
         A18DFElemId = IMSSOFFLIN27_A18DFElemId[0] ;
         A12DFFormVer = IMSSOFFLIN27_A12DFFormVer[0] ;
         A11DFFormId = IMSSOFFLIN27_A11DFFormId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A18DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A18DFElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A19DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A19DFElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A41DFFilElemFormElemId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A42DFFilElemFormElemVer, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A40DFFilElemFormId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A40DFFilElemFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A43DFFilElemFormPos, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A11DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A11DFFormId, (byte)(6), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A12DFFormVer, (byte)(6), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A12DFFormVer, (byte)(6), (byte)(0), ".", "")));
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
      /* Using cursor IMSSOFFLIN28 */
      pr_default.execute(26);
      while ( (pr_default.getStatus(26) != 101) )
      {
         A7HospitalId = IMSSOFFLIN28_A7HospitalId[0] ;
         n7HospitalId = IMSSOFFLIN28_n7HospitalId[0] ;
         A104ServicioDescripcion = IMSSOFFLIN28_A104ServicioDescripcion[0] ;
         A6ServicioId = IMSSOFFLIN28_A6ServicioId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A7HospitalId, (byte)(4), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.rtrim( A104ServicioDescripcion));
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
         pr_default.readNext(26);
      }
      pr_default.close(26);
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

   /*  Synchronize for table (Partial)  SIC_ESPECIALIDAD */
   public com.genexus.GxUnknownObjectCollection gxSyncEvtSIC_ESPECIALIDAD( )
   {
      /* Begin Synchronize  SIC_ESPECIALIDAD */
      /* Synchronization Type By Row */
      gxsyncheader.add("GXTable");
      gxsyncheader.add("SIC_ESPECIALIDAD");
      gxsyncresponse.add(gxsyncheader);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      /* Using cursor IMSSOFFLIN29 */
      pr_default.execute(27);
      while ( (pr_default.getStatus(27) != 101) )
      {
         A12DFFormVer = IMSSOFFLIN29_A12DFFormVer[0] ;
         A11DFFormId = IMSSOFFLIN29_A11DFFormId[0] ;
         A321fecBajaEspecialidad = IMSSOFFLIN29_A321fecBajaEspecialidad[0] ;
         n321fecBajaEspecialidad = IMSSOFFLIN29_n321fecBajaEspecialidad[0] ;
         A320desEspecialidad = IMSSOFFLIN29_A320desEspecialidad[0] ;
         A71cveEspecialidad = IMSSOFFLIN29_A71cveEspecialidad[0] ;
         A321fecBajaEspecialidad = IMSSOFFLIN29_A321fecBajaEspecialidad[0] ;
         n321fecBajaEspecialidad = IMSSOFFLIN29_n321fecBajaEspecialidad[0] ;
         A320desEspecialidad = IMSSOFFLIN29_A320desEspecialidad[0] ;
         gxsyncline.add(GXutil.rtrim( A71cveEspecialidad));
         gxsynchashkey.add(GXutil.rtrim( A71cveEspecialidad));
         gxsyncline.add(A320desEspecialidad);
         gxsyncline.add(GXutil.dateToCharREST( A321fecBajaEspecialidad));
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
         pr_default.readNext(27);
      }
      pr_default.close(27);
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
            new gxrowlevelcache(remoteHandle, context).execute ( gxdeviceidentifier ,  "SIC_ESPECIALIDAD" ,  gxtablecurrenthash ,  gxtablestoredhash ,  gxsyncvalueset ,  gxsynchashset ,  GXv_objcol_gxjsonable7 ,  GXv_objcol_gxjsonable6 ,  GXv_objcol_gxjsonable5 ,  GXv_int8 );
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
      gxsyncresponse_hash = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncresponse_hash.add(gxsyncheader);
      gxsyncline_hash = new com.genexus.internet.StringCollection() ;
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncvalueset = new com.genexus.GxUnknownObjectCollection() ;
      gxsynchashkey = new com.genexus.internet.StringCollection() ;
      gxfinalsync = new com.genexus.GxUnknownObjectCollection() ;
      pr_default.dynParam(28, new Object[]{ new Object[]{
                                           new Long(A9DFFormInstId) ,
                                           AV2ColDFFormInstId },
                                           new int[] {
                                           TypeConstants.LONG, TypeConstants.OBJECT_COLLECTION
                                           }
      });
      /* Using cursor IMSSOFFLIN30 */
      pr_default.execute(28);
      while ( (pr_default.getStatus(28) != 101) )
      {
         A28DFFormInstFormId = IMSSOFFLIN30_A28DFFormInstFormId[0] ;
         A139DFUplFileExt = IMSSOFFLIN30_A139DFUplFileExt[0] ;
         A140DFUplFileName = IMSSOFFLIN30_A140DFUplFileName[0] ;
         A138DFUplFile = IMSSOFFLIN30_A138DFUplFile[0] ;
         A10DFUplKey = IMSSOFFLIN30_A10DFUplKey[0] ;
         A9DFFormInstId = IMSSOFFLIN30_A9DFFormInstId[0] ;
         A28DFFormInstFormId = IMSSOFFLIN30_A28DFFormInstFormId[0] ;
         gxsyncline.add(GXutil.ltrim( localUtil.ntoc( A9DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsyncline_hash.add(GXutil.ltrim( localUtil.ntoc( A9DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsynchashkey.add(GXutil.ltrim( localUtil.ntoc( A9DFFormInstId, (byte)(10), (byte)(0), ".", "")));
         gxsyncline.add(GXutil.getRelativeBlobFile( A138DFUplFile));
         /* Blob file name not included in hash compute */
         gxsyncline.add(GXutil.rtrim( A139DFUplFileExt));
         gxsyncline_hash.add(GXutil.rtrim( A139DFUplFileExt));
         gxsyncline.add(GXutil.rtrim( A140DFUplFileName));
         gxsyncline_hash.add(GXutil.rtrim( A140DFUplFileName));
         gxsyncline.add(GXutil.rtrim( A10DFUplKey));
         gxsyncline_hash.add(GXutil.rtrim( A10DFUplKey));
         gxsynchashkey.add(GXutil.rtrim( A10DFUplKey));
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
         pr_default.readNext(28);
      }
      pr_default.close(28);
      /* End Synchronize */
      gxtabledata = gxsyncresponse.toJSonString(false) ;
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
      gxsyncheaderline.add("HMliKjjJzk+W2RG6VATtSQ==");
      gxallsyncresponse.add(gxsyncheaderline);
      gxsyncline = new com.genexus.internet.StringCollection() ;
      gxsynchashset = new com.genexus.GxUnknownObjectCollection() ;
      gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
      gxsourcever = gxhttpr.getHeader("GXSynchronizerVersion") ;
      if ( GXutil.strcmp(gxsourcever, "HMliKjjJzk+W2RG6VATtSQ==") != 0 )
      {
         gxerrorstatus = (short)(3) ;
      }
      if ( gxerrorstatus == 0 )
      {
         if ( gxtablehashlist.size() < 29 )
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
            gxtablemdata.add("DFParm");
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
            gxtablemdata.add("Extension");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("FormatoPaciente");
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
            gxtablemdata.add("DFForm");
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
            gxtablemdata.add("EspecialidadFormato");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("PacienteDiagnostico");
            gxtablemdata.add("");
            gxtablehashlist.add(gxtablemdata);
            gxtablemdata = new com.genexus.internet.StringCollection() ;
            gxtablemdata.add("DFDom");
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
            gxtablemdata.add("SIC_ESPECIALIDAD");
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
            else if ( GXutil.strcmp("DFParm", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDFParm( ) ;
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
            else if ( GXutil.strcmp("Extension", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtExtension( ) ;
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
            else if ( GXutil.strcmp("DFForm", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtDFForm( ) ;
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
            else if ( GXutil.strcmp("EspecialidadFormato", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtEspecialidadFormato( ) ;
               if ( gxischeck == 0 )
               {
                  gxallsyncresponse.add(gxsyncresponse);
                  gxsyncresponse = new com.genexus.GxUnknownObjectCollection() ;
               }
            }
            else if ( GXutil.strcmp("PacienteDiagnostico", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtPacienteDiagnostico( ) ;
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
            else if ( GXutil.strcmp("SIC_ESPECIALIDAD", gxtablemdata.item(1)) == 0 )
            {
               gxSyncEvtSIC_ESPECIALIDAD( ) ;
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
      IMSSOFFLIN2_A341FecBajaMed = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN2_n341FecBajaMed = new boolean[] {false} ;
      IMSSOFFLIN2_A303MedDebMosTerm = new boolean[] {false} ;
      IMSSOFFLIN2_n303MedDebMosTerm = new boolean[] {false} ;
      IMSSOFFLIN2_A295MedDebValDat = new boolean[] {false} ;
      IMSSOFFLIN2_A293MedUltAct = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN2_A340MedCedProf = new String[] {""} ;
      IMSSOFFLIN2_A291MedApMat = new String[] {""} ;
      IMSSOFFLIN2_A290MedApPat = new String[] {""} ;
      IMSSOFFLIN2_A288MedNom = new String[] {""} ;
      IMSSOFFLIN2_A64UserMed = new String[] {""} ;
      IMSSOFFLIN2_A65MedMatricula = new long[1] ;
      A341FecBajaMed = GXutil.nullDate() ;
      A293MedUltAct = GXutil.resetTime( GXutil.nullDate() );
      A340MedCedProf = "" ;
      A291MedApMat = "" ;
      A290MedApPat = "" ;
      A288MedNom = "" ;
      A64UserMed = "" ;
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
      A133PacienteNSSAgregado = "" ;
      A8Matricula = "" ;
      IMSSOFFLIN3_A133PacienteNSSAgregado = new String[] {""} ;
      IMSSOFFLIN3_A8Matricula = new String[] {""} ;
      IMSSOFFLIN3_A3PacienteAgregado = new String[] {""} ;
      IMSSOFFLIN3_A2PacienteNSS = new String[] {""} ;
      A3PacienteAgregado = "" ;
      A2PacienteNSS = "" ;
      IMSSOFFLIN4_A167DFParmIsMetaData = new boolean[] {false} ;
      IMSSOFFLIN4_A166DFParmVal = new String[] {""} ;
      IMSSOFFLIN4_A165DFParmName = new String[] {""} ;
      IMSSOFFLIN4_A25DFParmId = new int[1] ;
      A166DFParmVal = "" ;
      A165DFParmName = "" ;
      IMSSOFFLIN5_A76CIE10Descripcion = new String[] {""} ;
      IMSSOFFLIN5_A127CIECodigo = new String[] {""} ;
      IMSSOFFLIN5_A1CIE10Id = new int[1] ;
      A76CIE10Descripcion = "" ;
      A127CIECodigo = "" ;
      IMSSOFFLIN6_A133PacienteNSSAgregado = new String[] {""} ;
      IMSSOFFLIN6_A102MMatricula = new short[1] ;
      IMSSOFFLIN6_n102MMatricula = new boolean[] {false} ;
      IMSSOFFLIN6_A101MApMat = new short[1] ;
      IMSSOFFLIN6_n101MApMat = new boolean[] {false} ;
      IMSSOFFLIN6_A100MApPat = new short[1] ;
      IMSSOFFLIN6_n100MApPat = new boolean[] {false} ;
      IMSSOFFLIN6_A99MNombre = new short[1] ;
      IMSSOFFLIN6_n99MNombre = new boolean[] {false} ;
      IMSSOFFLIN6_A98MBMatricula = new short[1] ;
      IMSSOFFLIN6_n98MBMatricula = new boolean[] {false} ;
      IMSSOFFLIN6_A97MBApMat = new String[] {""} ;
      IMSSOFFLIN6_n97MBApMat = new boolean[] {false} ;
      IMSSOFFLIN6_A96MBApPat = new String[] {""} ;
      IMSSOFFLIN6_n96MBApPat = new boolean[] {false} ;
      IMSSOFFLIN6_A95MBNombre = new String[] {""} ;
      IMSSOFFLIN6_n95MBNombre = new boolean[] {false} ;
      IMSSOFFLIN6_A94JSMatricula = new short[1] ;
      IMSSOFFLIN6_n94JSMatricula = new boolean[] {false} ;
      IMSSOFFLIN6_A93JSApMat = new String[] {""} ;
      IMSSOFFLIN6_n93JSApMat = new boolean[] {false} ;
      IMSSOFFLIN6_A92JSApPat = new String[] {""} ;
      IMSSOFFLIN6_n92JSApPat = new boolean[] {false} ;
      IMSSOFFLIN6_A91JSNombre = new String[] {""} ;
      IMSSOFFLIN6_n91JSNombre = new boolean[] {false} ;
      IMSSOFFLIN6_A90DiagnosticoCirugiaFecha = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN6_n90DiagnosticoCirugiaFecha = new boolean[] {false} ;
      IMSSOFFLIN6_A89DiagnosticoCirugia = new String[] {""} ;
      IMSSOFFLIN6_n89DiagnosticoCirugia = new boolean[] {false} ;
      IMSSOFFLIN6_A88Cama = new String[] {""} ;
      IMSSOFFLIN6_n88Cama = new boolean[] {false} ;
      IMSSOFFLIN6_A6ServicioId = new short[1] ;
      IMSSOFFLIN6_A86DiagnosticoComplemento = new String[] {""} ;
      IMSSOFFLIN6_n86DiagnosticoComplemento = new boolean[] {false} ;
      IMSSOFFLIN6_A87DiagnosticoResumen = new String[] {""} ;
      IMSSOFFLIN6_n87DiagnosticoResumen = new boolean[] {false} ;
      IMSSOFFLIN6_A103DiagnosticoFechaAlta = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN6_n103DiagnosticoFechaAlta = new boolean[] {false} ;
      IMSSOFFLIN6_A85DiagnosticoFechaIngreso = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN6_n85DiagnosticoFechaIngreso = new boolean[] {false} ;
      IMSSOFFLIN6_A1CIE10Id = new int[1] ;
      IMSSOFFLIN6_A3PacienteAgregado = new String[] {""} ;
      IMSSOFFLIN6_A2PacienteNSS = new String[] {""} ;
      A97MBApMat = "" ;
      A96MBApPat = "" ;
      A95MBNombre = "" ;
      A93JSApMat = "" ;
      A92JSApPat = "" ;
      A91JSNombre = "" ;
      A90DiagnosticoCirugiaFecha = GXutil.resetTime( GXutil.nullDate() );
      A89DiagnosticoCirugia = "" ;
      A88Cama = "" ;
      A86DiagnosticoComplemento = "" ;
      A87DiagnosticoResumen = "" ;
      A103DiagnosticoFechaAlta = GXutil.resetTime( GXutil.nullDate() );
      A85DiagnosticoFechaIngreso = GXutil.nullDate() ;
      IMSSOFFLIN7_A314nada = new short[1] ;
      IMSSOFFLIN7_A302TextoDescripcion = new String[] {""} ;
      IMSSOFFLIN7_A301TextoTitulo = new String[] {""} ;
      IMSSOFFLIN7_A67TextoId = new short[1] ;
      A302TextoDescripcion = "" ;
      A301TextoTitulo = "" ;
      IMSSOFFLIN8_A133PacienteNSSAgregado = new String[] {""} ;
      IMSSOFFLIN8_A40000DXAuxImagenImg_GXI = new String[] {""} ;
      IMSSOFFLIN8_A84DXAuxImagenUserAlta = new String[] {""} ;
      IMSSOFFLIN8_A83DXAuxImagenFechaAlta = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN8_A82DXAuxImagenImg = new String[] {""} ;
      IMSSOFFLIN8_A313DXAuxImagenExtension = new String[] {""} ;
      IMSSOFFLIN8_A132DXAuxImagenNombre = new String[] {""} ;
      IMSSOFFLIN8_A5DXAuxImagenId = new short[1] ;
      IMSSOFFLIN8_A1CIE10Id = new int[1] ;
      IMSSOFFLIN8_A3PacienteAgregado = new String[] {""} ;
      IMSSOFFLIN8_A2PacienteNSS = new String[] {""} ;
      A40000DXAuxImagenImg_GXI = "" ;
      A84DXAuxImagenUserAlta = "" ;
      A83DXAuxImagenFechaAlta = GXutil.resetTime( GXutil.nullDate() );
      A82DXAuxImagenImg = "" ;
      A313DXAuxImagenExtension = "" ;
      A132DXAuxImagenNombre = "" ;
      gxsyncline_hash = new com.genexus.internet.StringCollection();
      gxsyncresponse_hash = new com.genexus.GxUnknownObjectCollection();
      IMSSOFFLIN9_A133PacienteNSSAgregado = new String[] {""} ;
      IMSSOFFLIN9_A79DXAuxDoctoNombre = new String[] {""} ;
      IMSSOFFLIN9_A78DXAuxDoctoExtension = new String[] {""} ;
      IMSSOFFLIN9_A81DXAuxDoctoUserAlta = new String[] {""} ;
      IMSSOFFLIN9_A80DXAuxDoctoFechaAlta = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN9_A77DXAuxDoctoDocumento = new String[] {""} ;
      IMSSOFFLIN9_A4DXAuxDoctoId = new short[1] ;
      IMSSOFFLIN9_A1CIE10Id = new int[1] ;
      IMSSOFFLIN9_A3PacienteAgregado = new String[] {""} ;
      IMSSOFFLIN9_A2PacienteNSS = new String[] {""} ;
      A79DXAuxDoctoNombre = "" ;
      A78DXAuxDoctoExtension = "" ;
      A81DXAuxDoctoUserAlta = "" ;
      A80DXAuxDoctoFechaAlta = GXutil.resetTime( GXutil.nullDate() );
      A77DXAuxDoctoDocumento = "" ;
      IMSSOFFLIN10_A330ClavePresupuestal = new String[] {""} ;
      IMSSOFFLIN10_A328IDEE = new String[] {""} ;
      IMSSOFFLIN10_n328IDEE = new boolean[] {false} ;
      IMSSOFFLIN10_A325CURP = new String[] {""} ;
      IMSSOFFLIN10_n325CURP = new boolean[] {false} ;
      IMSSOFFLIN10_A327DhUMF = new String[] {""} ;
      IMSSOFFLIN10_n327DhUMF = new boolean[] {false} ;
      IMSSOFFLIN10_A326DhDeleg = new String[] {""} ;
      IMSSOFFLIN10_n326DhDeleg = new boolean[] {false} ;
      IMSSOFFLIN10_A324Consultorio = new String[] {""} ;
      IMSSOFFLIN10_n324Consultorio = new boolean[] {false} ;
      IMSSOFFLIN10_A323ConDerechoSm = new String[] {""} ;
      IMSSOFFLIN10_n323ConDerechoSm = new boolean[] {false} ;
      IMSSOFFLIN10_A322ConDerechoInc = new String[] {""} ;
      IMSSOFFLIN10_n322ConDerechoInc = new boolean[] {false} ;
      IMSSOFFLIN10_A312PacienteServicioId = new short[1] ;
      IMSSOFFLIN10_A130PacienteCie10Id = new int[1] ;
      IMSSOFFLIN10_A133PacienteNSSAgregado = new String[] {""} ;
      IMSSOFFLIN10_A131PacienteCama = new String[] {""} ;
      IMSSOFFLIN10_A287PacienteDiagnosticoPhone = new String[] {""} ;
      IMSSOFFLIN10_A129PacienteDiagnosticoResumido = new String[] {""} ;
      IMSSOFFLIN10_A128PacienteDiagnostico = new String[] {""} ;
      IMSSOFFLIN10_A134PAcienteFechaIngreso = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN10_A124PacienteNombreCompleto = new String[] {""} ;
      IMSSOFFLIN10_A123PacienteReferencia = new String[] {""} ;
      IMSSOFFLIN10_n123PacienteReferencia = new boolean[] {false} ;
      IMSSOFFLIN10_A122PacienteFamiliar = new String[] {""} ;
      IMSSOFFLIN10_n122PacienteFamiliar = new boolean[] {false} ;
      IMSSOFFLIN10_A121PacienteTelefono = new String[] {""} ;
      IMSSOFFLIN10_n121PacienteTelefono = new boolean[] {false} ;
      IMSSOFFLIN10_A120PacienteGenero = new String[] {""} ;
      IMSSOFFLIN10_n120PacienteGenero = new boolean[] {false} ;
      IMSSOFFLIN10_A118PacienteEdad = new short[1] ;
      IMSSOFFLIN10_A119PacienteFechaNacimiento = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN10_A114PacienteApMat = new String[] {""} ;
      IMSSOFFLIN10_n114PacienteApMat = new boolean[] {false} ;
      IMSSOFFLIN10_A113PacienteApPat = new String[] {""} ;
      IMSSOFFLIN10_A112PacienteNombre = new String[] {""} ;
      IMSSOFFLIN10_A3PacienteAgregado = new String[] {""} ;
      IMSSOFFLIN10_A2PacienteNSS = new String[] {""} ;
      A330ClavePresupuestal = "" ;
      A328IDEE = "" ;
      A325CURP = "" ;
      A327DhUMF = "" ;
      A326DhDeleg = "" ;
      A324Consultorio = "" ;
      A323ConDerechoSm = "" ;
      A322ConDerechoInc = "" ;
      A131PacienteCama = "" ;
      A287PacienteDiagnosticoPhone = "" ;
      A129PacienteDiagnosticoResumido = "" ;
      A128PacienteDiagnostico = "" ;
      A134PAcienteFechaIngreso = GXutil.nullDate() ;
      A124PacienteNombreCompleto = "" ;
      A123PacienteReferencia = "" ;
      A122PacienteFamiliar = "" ;
      A121PacienteTelefono = "" ;
      A120PacienteGenero = "" ;
      A119PacienteFechaNacimiento = GXutil.nullDate() ;
      A114PacienteApMat = "" ;
      A113PacienteApPat = "" ;
      A112PacienteNombre = "" ;
      IMSSOFFLIN11_A297ExtensionNombre = new String[] {""} ;
      IMSSOFFLIN11_A296ExtensionTipo = new short[1] ;
      IMSSOFFLIN11_A66ExtensionId = new short[1] ;
      A297ExtensionNombre = "" ;
      IMSSOFFLIN12_A136FormatoPacienteMedicoMatricula = new long[1] ;
      IMSSOFFLIN12_A137FormatoPacienteMedicoNombre = new String[] {""} ;
      IMSSOFFLIN12_A9DFFormInstId = new long[1] ;
      IMSSOFFLIN12_A63FormatoPacienteAgregado = new String[] {""} ;
      IMSSOFFLIN12_A62FormatoPacienteNSS = new String[] {""} ;
      A137FormatoPacienteMedicoNombre = "" ;
      A63FormatoPacienteAgregado = "" ;
      A62FormatoPacienteNSS = "" ;
      IMSSOFFLIN13_A304DFElemFormReq = new boolean[] {false} ;
      IMSSOFFLIN13_A299DFElemFormLoadRule = new String[] {""} ;
      IMSSOFFLIN13_n299DFElemFormLoadRule = new boolean[] {false} ;
      IMSSOFFLIN13_A263DFElemFormMetadata = new String[] {""} ;
      IMSSOFFLIN13_n263DFElemFormMetadata = new boolean[] {false} ;
      IMSSOFFLIN13_A264DFElemFormShwNbr = new boolean[] {false} ;
      IMSSOFFLIN13_n264DFElemFormShwNbr = new boolean[] {false} ;
      IMSSOFFLIN13_A262DFElemFormDateSel = new boolean[] {false} ;
      IMSSOFFLIN13_n262DFElemFormDateSel = new boolean[] {false} ;
      IMSSOFFLIN13_A259DFElemFormHasPmpt = new boolean[] {false} ;
      IMSSOFFLIN13_n259DFElemFormHasPmpt = new boolean[] {false} ;
      IMSSOFFLIN13_A184DFElemFormIsFlt = new String[] {""} ;
      IMSSOFFLIN13_n184DFElemFormIsFlt = new boolean[] {false} ;
      IMSSOFFLIN13_A183DFElemFormCmpWth = new String[] {""} ;
      IMSSOFFLIN13_n183DFElemFormCmpWth = new boolean[] {false} ;
      IMSSOFFLIN13_A182DFElemFormLblWth = new String[] {""} ;
      IMSSOFFLIN13_n182DFElemFormLblWth = new boolean[] {false} ;
      IMSSOFFLIN13_A307DFElemFormPrtPic = new String[] {""} ;
      IMSSOFFLIN13_A282DFElemFormPrtShwNbr = new boolean[] {false} ;
      IMSSOFFLIN13_A281DFElemFormPrtNumColSkip = new int[1] ;
      IMSSOFFLIN13_A273DFElemFormPrtNumRowSkip = new int[1] ;
      IMSSOFFLIN13_A271DFElemFormPrtAddRows = new boolean[] {false} ;
      IMSSOFFLIN13_A270DFElemFormPrtName = new String[] {""} ;
      IMSSOFFLIN13_A191DFElemFormIsVisPrt = new boolean[] {false} ;
      IMSSOFFLIN13_A190DFElemFormIsVis = new boolean[] {false} ;
      IMSSOFFLIN13_A189DFElemFormIsColap = new boolean[] {false} ;
      IMSSOFFLIN13_A188DFElemFormAllowIns = new boolean[] {false} ;
      IMSSOFFLIN13_n188DFElemFormAllowIns = new boolean[] {false} ;
      IMSSOFFLIN13_A187DFElemFormAllowUpd = new boolean[] {false} ;
      IMSSOFFLIN13_n187DFElemFormAllowUpd = new boolean[] {false} ;
      IMSSOFFLIN13_A186DFElemFormAllowDlt = new boolean[] {false} ;
      IMSSOFFLIN13_n186DFElemFormAllowDlt = new boolean[] {false} ;
      IMSSOFFLIN13_A181DFElemFormInhType = new String[] {""} ;
      IMSSOFFLIN13_A36DFElemFormPos = new int[1] ;
      IMSSOFFLIN13_A185DFElemFormName = new String[] {""} ;
      IMSSOFFLIN13_A19DFElemVer = new int[1] ;
      IMSSOFFLIN13_A18DFElemId = new int[1] ;
      IMSSOFFLIN13_A12DFFormVer = new int[1] ;
      IMSSOFFLIN13_A11DFFormId = new int[1] ;
      A299DFElemFormLoadRule = "" ;
      A263DFElemFormMetadata = "" ;
      A184DFElemFormIsFlt = "" ;
      A183DFElemFormCmpWth = "" ;
      A182DFElemFormLblWth = "" ;
      A307DFElemFormPrtPic = "" ;
      A270DFElemFormPrtName = "" ;
      A181DFElemFormInhType = "" ;
      A185DFElemFormName = "" ;
      IMSSOFFLIN14_A145DFElemFormInstFileName = new String[] {""} ;
      IMSSOFFLIN14_n145DFElemFormInstFileName = new boolean[] {false} ;
      IMSSOFFLIN14_A144DFElemFormInstFileType = new String[] {""} ;
      IMSSOFFLIN14_n144DFElemFormInstFileType = new boolean[] {false} ;
      IMSSOFFLIN14_A143DFElemFormInstBlob = new String[] {""} ;
      IMSSOFFLIN14_n143DFElemFormInstBlob = new boolean[] {false} ;
      IMSSOFFLIN14_A141DFElemFormInstVal = new String[] {""} ;
      IMSSOFFLIN14_n141DFElemFormInstVal = new boolean[] {false} ;
      IMSSOFFLIN14_A19DFElemVer = new int[1] ;
      IMSSOFFLIN14_A18DFElemId = new int[1] ;
      IMSSOFFLIN14_A9DFFormInstId = new long[1] ;
      A145DFElemFormInstFileName = "" ;
      A144DFElemFormInstFileType = "" ;
      A143DFElemFormInstBlob = "" ;
      A141DFElemFormInstVal = "" ;
      IMSSOFFLIN15_A148DFElemFormInstSubElemFileName = new String[] {""} ;
      IMSSOFFLIN15_n148DFElemFormInstSubElemFileName = new boolean[] {false} ;
      IMSSOFFLIN15_A147DFElemFormInstSubElemFileType = new String[] {""} ;
      IMSSOFFLIN15_n147DFElemFormInstSubElemFileType = new boolean[] {false} ;
      IMSSOFFLIN15_A37DFSubElemFormElemId = new int[1] ;
      IMSSOFFLIN15_A38DFSubElemFormElemVer = new int[1] ;
      IMSSOFFLIN15_A69DFElemFormInstSubElemRow = new int[1] ;
      IMSSOFFLIN15_A142DFElemFormInstSubElemVal = new String[] {""} ;
      IMSSOFFLIN15_n142DFElemFormInstSubElemVal = new boolean[] {false} ;
      IMSSOFFLIN15_A146DFElemFormInstSubElemBlob = new String[] {""} ;
      IMSSOFFLIN15_n146DFElemFormInstSubElemBlob = new boolean[] {false} ;
      IMSSOFFLIN15_A68DFElemFormInstSubElemId = new int[1] ;
      IMSSOFFLIN15_A19DFElemVer = new int[1] ;
      IMSSOFFLIN15_A18DFElemId = new int[1] ;
      IMSSOFFLIN15_A9DFFormInstId = new long[1] ;
      A148DFElemFormInstSubElemFileName = "" ;
      A147DFElemFormInstSubElemFileType = "" ;
      A142DFElemFormInstSubElemVal = "" ;
      A146DFElemFormInstSubElemBlob = "" ;
      IMSSOFFLIN16_A284DFTempOutFm = new String[] {""} ;
      IMSSOFFLIN16_A278DFTempAddParmPrgName = new String[] {""} ;
      IMSSOFFLIN16_A277DFTempBlob = new String[] {""} ;
      IMSSOFFLIN16_A286DFTempFm = new String[] {""} ;
      IMSSOFFLIN16_A283DFTempDsc = new String[] {""} ;
      IMSSOFFLIN16_A55DFTempName = new String[] {""} ;
      IMSSOFFLIN16_A12DFFormVer = new int[1] ;
      IMSSOFFLIN16_A11DFFormId = new int[1] ;
      A284DFTempOutFm = "" ;
      A278DFTempAddParmPrgName = "" ;
      A277DFTempBlob = "" ;
      A286DFTempFm = "" ;
      A283DFTempDsc = "" ;
      A55DFTempName = "" ;
      IMSSOFFLIN17_A298DFFormIsSD = new boolean[] {false} ;
      IMSSOFFLIN17_A157DFFormRunDLT = new boolean[] {false} ;
      IMSSOFFLIN17_A233DFFormHelpURL = new String[] {""} ;
      IMSSOFFLIN17_A173DFFormPrefix = new String[] {""} ;
      IMSSOFFLIN17_A232DFFormPmtHgh = new int[1] ;
      IMSSOFFLIN17_n232DFFormPmtHgh = new boolean[] {false} ;
      IMSSOFFLIN17_A231DFFormPmtWth = new int[1] ;
      IMSSOFFLIN17_n231DFFormPmtWth = new boolean[] {false} ;
      IMSSOFFLIN17_A234DFFormAct = new boolean[] {false} ;
      IMSSOFFLIN17_A308DFFormDsc = new String[] {""} ;
      IMSSOFFLIN17_A31DFFormName = new String[] {""} ;
      IMSSOFFLIN17_A30DFFormGuid = new java.util.UUID[] {java.util.UUID.fromString("00000000-0000-0000-0000-000000000000")} ;
      IMSSOFFLIN17_A12DFFormVer = new int[1] ;
      IMSSOFFLIN17_A11DFFormId = new int[1] ;
      A233DFFormHelpURL = "" ;
      A173DFFormPrefix = "" ;
      A308DFFormDsc = "" ;
      A31DFFormName = "" ;
      A30DFFormGuid = java.util.UUID.fromString("00000000-0000-0000-0000-000000000000") ;
      IMSSOFFLIN18_A222DFDomStaValOptDsc = new String[] {""} ;
      IMSSOFFLIN18_A34DFDomStaValOptOrd = new int[1] ;
      IMSSOFFLIN18_A33DFDomStaValOptCod = new String[] {""} ;
      IMSSOFFLIN18_A32DFDomId = new int[1] ;
      IMSSOFFLIN18_n32DFDomId = new boolean[] {false} ;
      A222DFDomStaValOptDsc = "" ;
      A33DFDomStaValOptCod = "" ;
      IMSSOFFLIN19_A197DFFormInstSignedPDF = new String[] {""} ;
      IMSSOFFLIN19_n197DFFormInstSignedPDF = new boolean[] {false} ;
      IMSSOFFLIN19_A198DFFormInstSignedBy = new String[] {""} ;
      IMSSOFFLIN19_n198DFFormInstSignedBy = new boolean[] {false} ;
      IMSSOFFLIN19_A155DFFormInstDT = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN19_A29DFFormInstFormVer = new int[1] ;
      IMSSOFFLIN19_A28DFFormInstFormId = new int[1] ;
      IMSSOFFLIN19_A9DFFormInstId = new long[1] ;
      A197DFFormInstSignedPDF = "" ;
      A198DFFormInstSignedBy = "" ;
      A155DFFormInstDT = GXutil.resetTime( GXutil.nullDate() );
      IMSSOFFLIN20_A305DFElemReq = new boolean[] {false} ;
      IMSSOFFLIN20_A300DFElemLoadRule = new String[] {""} ;
      IMSSOFFLIN20_n300DFElemLoadRule = new boolean[] {false} ;
      IMSSOFFLIN20_A265DFElemMetadata = new String[] {""} ;
      IMSSOFFLIN20_n265DFElemMetadata = new boolean[] {false} ;
      IMSSOFFLIN20_A238DFElemIsColap = new boolean[] {false} ;
      IMSSOFFLIN20_A306DFElemPrtPic = new String[] {""} ;
      IMSSOFFLIN20_A280DFElemPrtShwNbr = new boolean[] {false} ;
      IMSSOFFLIN20_A279DFElemPrtNumColSkip = new int[1] ;
      IMSSOFFLIN20_A274DFElemPrtNumRowSkip = new int[1] ;
      IMSSOFFLIN20_A272DFElemPrtAddRows = new boolean[] {false} ;
      IMSSOFFLIN20_A269DFElemPrtName = new String[] {""} ;
      IMSSOFFLIN20_A260DFElemIsVisPrt = new boolean[] {false} ;
      IMSSOFFLIN20_A237DFElemIsVis = new boolean[] {false} ;
      IMSSOFFLIN20_A257DFElemLblWth = new String[] {""} ;
      IMSSOFFLIN20_n257DFElemLblWth = new boolean[] {false} ;
      IMSSOFFLIN20_A243DFElemCmpWth = new String[] {""} ;
      IMSSOFFLIN20_n243DFElemCmpWth = new boolean[] {false} ;
      IMSSOFFLIN20_A242DFElemIsFlt = new String[] {""} ;
      IMSSOFFLIN20_n242DFElemIsFlt = new boolean[] {false} ;
      IMSSOFFLIN20_A256DFElemFileType = new String[] {""} ;
      IMSSOFFLIN20_n256DFElemFileType = new boolean[] {false} ;
      IMSSOFFLIN20_A254DFElemRegexVal = new String[] {""} ;
      IMSSOFFLIN20_n254DFElemRegexVal = new boolean[] {false} ;
      IMSSOFFLIN20_A253DFElemAllowDlt = new boolean[] {false} ;
      IMSSOFFLIN20_n253DFElemAllowDlt = new boolean[] {false} ;
      IMSSOFFLIN20_A252DFElemAllowUpd = new boolean[] {false} ;
      IMSSOFFLIN20_n252DFElemAllowUpd = new boolean[] {false} ;
      IMSSOFFLIN20_A251DFElemAllowIns = new boolean[] {false} ;
      IMSSOFFLIN20_n251DFElemAllowIns = new boolean[] {false} ;
      IMSSOFFLIN20_A250DFElemUseBtns = new boolean[] {false} ;
      IMSSOFFLIN20_n250DFElemUseBtns = new boolean[] {false} ;
      IMSSOFFLIN20_A249DFElemIsOrd = new boolean[] {false} ;
      IMSSOFFLIN20_n249DFElemIsOrd = new boolean[] {false} ;
      IMSSOFFLIN20_A248DFElemMaxSuggRes = new int[1] ;
      IMSSOFFLIN20_n248DFElemMaxSuggRes = new boolean[] {false} ;
      IMSSOFFLIN20_A247DFElemForceSuggSel = new boolean[] {false} ;
      IMSSOFFLIN20_n247DFElemForceSuggSel = new boolean[] {false} ;
      IMSSOFFLIN20_A246DFElemMinCntCharSugg = new int[1] ;
      IMSSOFFLIN20_n246DFElemMinCntCharSugg = new boolean[] {false} ;
      IMSSOFFLIN20_A258DFElemDscPrgName = new String[] {""} ;
      IMSSOFFLIN20_A245DFElemLoadPrgName = new String[] {""} ;
      IMSSOFFLIN20_n245DFElemLoadPrgName = new boolean[] {false} ;
      IMSSOFFLIN20_A267DFElemBtnPos = new String[] {""} ;
      IMSSOFFLIN20_n267DFElemBtnPos = new boolean[] {false} ;
      IMSSOFFLIN20_A268DFElemShwNbrLbl = new String[] {""} ;
      IMSSOFFLIN20_n268DFElemShwNbrLbl = new boolean[] {false} ;
      IMSSOFFLIN20_A266DFElemShwNbr = new boolean[] {false} ;
      IMSSOFFLIN20_n266DFElemShwNbr = new boolean[] {false} ;
      IMSSOFFLIN20_A261DFElemDateSel = new boolean[] {false} ;
      IMSSOFFLIN20_n261DFElemDateSel = new boolean[] {false} ;
      IMSSOFFLIN20_A244DFElemHasPmpt = new boolean[] {false} ;
      IMSSOFFLIN20_n244DFElemHasPmpt = new boolean[] {false} ;
      IMSSOFFLIN20_A180DFElemDftVal = new String[] {""} ;
      IMSSOFFLIN20_n180DFElemDftVal = new boolean[] {false} ;
      IMSSOFFLIN20_A241DFElemCntCols = new int[1] ;
      IMSSOFFLIN20_n241DFElemCntCols = new boolean[] {false} ;
      IMSSOFFLIN20_A240DFElemCntRows = new int[1] ;
      IMSSOFFLIN20_n240DFElemCntRows = new boolean[] {false} ;
      IMSSOFFLIN20_A239DFElemCntDec = new int[1] ;
      IMSSOFFLIN20_n239DFElemCntDec = new boolean[] {false} ;
      IMSSOFFLIN20_A255DFElemWth = new int[1] ;
      IMSSOFFLIN20_n255DFElemWth = new boolean[] {false} ;
      IMSSOFFLIN20_A236DFElemLen = new int[1] ;
      IMSSOFFLIN20_n236DFElemLen = new boolean[] {false} ;
      IMSSOFFLIN20_A196DFElemDsp = new String[] {""} ;
      IMSSOFFLIN20_n196DFElemDsp = new boolean[] {false} ;
      IMSSOFFLIN20_A178DFElemType = new String[] {""} ;
      IMSSOFFLIN20_A32DFDomId = new int[1] ;
      IMSSOFFLIN20_n32DFDomId = new boolean[] {false} ;
      IMSSOFFLIN20_A192DFElemClsName = new String[] {""} ;
      IMSSOFFLIN20_n192DFElemClsName = new boolean[] {false} ;
      IMSSOFFLIN20_A235DFElemDsc = new String[] {""} ;
      IMSSOFFLIN20_n235DFElemDsc = new boolean[] {false} ;
      IMSSOFFLIN20_A149DFElemName = new String[] {""} ;
      IMSSOFFLIN20_A35DFElemGuid = new java.util.UUID[] {java.util.UUID.fromString("00000000-0000-0000-0000-000000000000")} ;
      IMSSOFFLIN20_A19DFElemVer = new int[1] ;
      IMSSOFFLIN20_A18DFElemId = new int[1] ;
      A300DFElemLoadRule = "" ;
      A265DFElemMetadata = "" ;
      A306DFElemPrtPic = "" ;
      A269DFElemPrtName = "" ;
      A257DFElemLblWth = "" ;
      A243DFElemCmpWth = "" ;
      A242DFElemIsFlt = "" ;
      A256DFElemFileType = "" ;
      A254DFElemRegexVal = "" ;
      A258DFElemDscPrgName = "" ;
      A245DFElemLoadPrgName = "" ;
      A267DFElemBtnPos = "" ;
      A268DFElemShwNbrLbl = "" ;
      A180DFElemDftVal = "" ;
      A196DFElemDsp = "" ;
      A178DFElemType = "" ;
      A192DFElemClsName = "" ;
      A235DFElemDsc = "" ;
      A149DFElemName = "" ;
      A35DFElemGuid = java.util.UUID.fromString("00000000-0000-0000-0000-000000000000") ;
      IMSSOFFLIN21_A71cveEspecialidad = new String[] {""} ;
      IMSSOFFLIN21_A12DFFormVer = new int[1] ;
      IMSSOFFLIN21_A11DFFormId = new int[1] ;
      A71cveEspecialidad = "" ;
      IMSSOFFLIN22_A348PXDXFechaAsignacion = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN22_A347OcaSer = new short[1] ;
      IMSSOFFLIN22_A346TpoDX = new short[1] ;
      IMSSOFFLIN22_A345DX = new int[1] ;
      IMSSOFFLIN22_A353IDEEPaciente = new String[] {""} ;
      A348PXDXFechaAsignacion = GXutil.resetTime( GXutil.nullDate() );
      A353IDEEPaciente = "" ;
      IMSSOFFLIN23_A310DFDomPrtDsc = new boolean[] {false} ;
      IMSSOFFLIN23_n310DFDomPrtDsc = new boolean[] {false} ;
      IMSSOFFLIN23_A223DFDomLblWth = new String[] {""} ;
      IMSSOFFLIN23_n223DFDomLblWth = new boolean[] {false} ;
      IMSSOFFLIN23_A219DFDomCmpWth = new String[] {""} ;
      IMSSOFFLIN23_n219DFDomCmpWth = new boolean[] {false} ;
      IMSSOFFLIN23_A218DFDomIsFlt = new String[] {""} ;
      IMSSOFFLIN23_n218DFDomIsFlt = new boolean[] {false} ;
      IMSSOFFLIN23_A221DFDomFileType = new String[] {""} ;
      IMSSOFFLIN23_n221DFDomFileType = new boolean[] {false} ;
      IMSSOFFLIN23_A217DFDomRegexVal = new String[] {""} ;
      IMSSOFFLIN23_A213DFDomAllowDlt = new boolean[] {false} ;
      IMSSOFFLIN23_n213DFDomAllowDlt = new boolean[] {false} ;
      IMSSOFFLIN23_A212DFDomAllowUpd = new boolean[] {false} ;
      IMSSOFFLIN23_n212DFDomAllowUpd = new boolean[] {false} ;
      IMSSOFFLIN23_A211DFDomAllowIns = new boolean[] {false} ;
      IMSSOFFLIN23_n211DFDomAllowIns = new boolean[] {false} ;
      IMSSOFFLIN23_A210DFDomUseBtns = new boolean[] {false} ;
      IMSSOFFLIN23_n210DFDomUseBtns = new boolean[] {false} ;
      IMSSOFFLIN23_A209DFDomIsOrd = new boolean[] {false} ;
      IMSSOFFLIN23_n209DFDomIsOrd = new boolean[] {false} ;
      IMSSOFFLIN23_A207DFDomMaxSuggRes = new int[1] ;
      IMSSOFFLIN23_n207DFDomMaxSuggRes = new boolean[] {false} ;
      IMSSOFFLIN23_A206DFDomForceSuggSel = new boolean[] {false} ;
      IMSSOFFLIN23_n206DFDomForceSuggSel = new boolean[] {false} ;
      IMSSOFFLIN23_A205DFDomMinCntCharSugg = new int[1] ;
      IMSSOFFLIN23_n205DFDomMinCntCharSugg = new boolean[] {false} ;
      IMSSOFFLIN23_A208DFDomDftVal = new String[] {""} ;
      IMSSOFFLIN23_n208DFDomDftVal = new boolean[] {false} ;
      IMSSOFFLIN23_A216DFDomCntCols = new int[1] ;
      IMSSOFFLIN23_A215DFDomCntRows = new int[1] ;
      IMSSOFFLIN23_A214DFDomCntDec = new int[1] ;
      IMSSOFFLIN23_A220DFDomWth = new int[1] ;
      IMSSOFFLIN23_A204DFDomLen = new int[1] ;
      IMSSOFFLIN23_A195DFDomDsp = new String[] {""} ;
      IMSSOFFLIN23_n195DFDomDsp = new boolean[] {false} ;
      IMSSOFFLIN23_A194DFDomType = new String[] {""} ;
      IMSSOFFLIN23_A224DFDomGUID = new java.util.UUID[] {java.util.UUID.fromString("00000000-0000-0000-0000-000000000000")} ;
      IMSSOFFLIN23_A203DFDomDsc = new String[] {""} ;
      IMSSOFFLIN23_A32DFDomId = new int[1] ;
      IMSSOFFLIN23_n32DFDomId = new boolean[] {false} ;
      A223DFDomLblWth = "" ;
      A219DFDomCmpWth = "" ;
      A218DFDomIsFlt = "" ;
      A221DFDomFileType = "" ;
      A217DFDomRegexVal = "" ;
      A208DFDomDftVal = "" ;
      A195DFDomDsp = "" ;
      A194DFDomType = "" ;
      A224DFDomGUID = java.util.UUID.fromString("00000000-0000-0000-0000-000000000000") ;
      A203DFDomDsc = "" ;
      IMSSOFFLIN24_A14DFFormRstVal = new String[] {""} ;
      IMSSOFFLIN24_A13DFFormRstId = new int[1] ;
      IMSSOFFLIN24_A12DFFormVer = new int[1] ;
      IMSSOFFLIN24_A11DFFormId = new int[1] ;
      A14DFFormRstVal = "" ;
      IMSSOFFLIN25_A164DFUserRstPwdIni = new boolean[] {false} ;
      IMSSOFFLIN25_A24DFUserRstVal = new String[] {""} ;
      IMSSOFFLIN25_A23DFUserRstId = new int[1] ;
      IMSSOFFLIN25_A22DFUserExtId = new String[] {""} ;
      A24DFUserRstVal = "" ;
      A22DFUserExtId = "" ;
      IMSSOFFLIN26_A39DFSubElemFormPos = new int[1] ;
      IMSSOFFLIN26_n39DFSubElemFormPos = new boolean[] {false} ;
      IMSSOFFLIN26_A38DFSubElemFormElemVer = new int[1] ;
      IMSSOFFLIN26_A37DFSubElemFormElemId = new int[1] ;
      IMSSOFFLIN26_A19DFElemVer = new int[1] ;
      IMSSOFFLIN26_A18DFElemId = new int[1] ;
      IMSSOFFLIN26_A12DFFormVer = new int[1] ;
      IMSSOFFLIN26_A11DFFormId = new int[1] ;
      IMSSOFFLIN27_A42DFFilElemFormElemVer = new int[1] ;
      IMSSOFFLIN27_A41DFFilElemFormElemId = new int[1] ;
      IMSSOFFLIN27_A43DFFilElemFormPos = new short[1] ;
      IMSSOFFLIN27_A40DFFilElemFormId = new int[1] ;
      IMSSOFFLIN27_A19DFElemVer = new int[1] ;
      IMSSOFFLIN27_A18DFElemId = new int[1] ;
      IMSSOFFLIN27_A12DFFormVer = new int[1] ;
      IMSSOFFLIN27_A11DFFormId = new int[1] ;
      IMSSOFFLIN28_A7HospitalId = new short[1] ;
      IMSSOFFLIN28_n7HospitalId = new boolean[] {false} ;
      IMSSOFFLIN28_A104ServicioDescripcion = new String[] {""} ;
      IMSSOFFLIN28_A6ServicioId = new short[1] ;
      A104ServicioDescripcion = "" ;
      IMSSOFFLIN29_A12DFFormVer = new int[1] ;
      IMSSOFFLIN29_A11DFFormId = new int[1] ;
      IMSSOFFLIN29_A321fecBajaEspecialidad = new java.util.Date[] {GXutil.nullDate()} ;
      IMSSOFFLIN29_n321fecBajaEspecialidad = new boolean[] {false} ;
      IMSSOFFLIN29_A320desEspecialidad = new String[] {""} ;
      IMSSOFFLIN29_A71cveEspecialidad = new String[] {""} ;
      A321fecBajaEspecialidad = GXutil.nullDate() ;
      A320desEspecialidad = "" ;
      IMSSOFFLIN30_A28DFFormInstFormId = new int[1] ;
      IMSSOFFLIN30_A139DFUplFileExt = new String[] {""} ;
      IMSSOFFLIN30_A140DFUplFileName = new String[] {""} ;
      IMSSOFFLIN30_A138DFUplFile = new String[] {""} ;
      IMSSOFFLIN30_A10DFUplKey = new String[] {""} ;
      IMSSOFFLIN30_A9DFFormInstId = new long[1] ;
      A139DFUplFileExt = "" ;
      A140DFUplFileName = "" ;
      A138DFUplFile = "" ;
      A10DFUplKey = "" ;
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
            IMSSOFFLIN2_A341FecBajaMed, IMSSOFFLIN2_n341FecBajaMed, IMSSOFFLIN2_A303MedDebMosTerm, IMSSOFFLIN2_n303MedDebMosTerm, IMSSOFFLIN2_A295MedDebValDat, IMSSOFFLIN2_A293MedUltAct, IMSSOFFLIN2_A340MedCedProf, IMSSOFFLIN2_A291MedApMat, IMSSOFFLIN2_A290MedApPat, IMSSOFFLIN2_A288MedNom,
            IMSSOFFLIN2_A64UserMed, IMSSOFFLIN2_A65MedMatricula
            }
            , new Object[] {
            IMSSOFFLIN3_A133PacienteNSSAgregado, IMSSOFFLIN3_A8Matricula, IMSSOFFLIN3_A3PacienteAgregado, IMSSOFFLIN3_A2PacienteNSS
            }
            , new Object[] {
            IMSSOFFLIN4_A167DFParmIsMetaData, IMSSOFFLIN4_A166DFParmVal, IMSSOFFLIN4_A165DFParmName, IMSSOFFLIN4_A25DFParmId
            }
            , new Object[] {
            IMSSOFFLIN5_A76CIE10Descripcion, IMSSOFFLIN5_A127CIECodigo, IMSSOFFLIN5_A1CIE10Id
            }
            , new Object[] {
            IMSSOFFLIN6_A133PacienteNSSAgregado, IMSSOFFLIN6_A102MMatricula, IMSSOFFLIN6_n102MMatricula, IMSSOFFLIN6_A101MApMat, IMSSOFFLIN6_n101MApMat, IMSSOFFLIN6_A100MApPat, IMSSOFFLIN6_n100MApPat, IMSSOFFLIN6_A99MNombre, IMSSOFFLIN6_n99MNombre, IMSSOFFLIN6_A98MBMatricula,
            IMSSOFFLIN6_n98MBMatricula, IMSSOFFLIN6_A97MBApMat, IMSSOFFLIN6_n97MBApMat, IMSSOFFLIN6_A96MBApPat, IMSSOFFLIN6_n96MBApPat, IMSSOFFLIN6_A95MBNombre, IMSSOFFLIN6_n95MBNombre, IMSSOFFLIN6_A94JSMatricula, IMSSOFFLIN6_n94JSMatricula, IMSSOFFLIN6_A93JSApMat,
            IMSSOFFLIN6_n93JSApMat, IMSSOFFLIN6_A92JSApPat, IMSSOFFLIN6_n92JSApPat, IMSSOFFLIN6_A91JSNombre, IMSSOFFLIN6_n91JSNombre, IMSSOFFLIN6_A90DiagnosticoCirugiaFecha, IMSSOFFLIN6_n90DiagnosticoCirugiaFecha, IMSSOFFLIN6_A89DiagnosticoCirugia, IMSSOFFLIN6_n89DiagnosticoCirugia, IMSSOFFLIN6_A88Cama,
            IMSSOFFLIN6_n88Cama, IMSSOFFLIN6_A6ServicioId, IMSSOFFLIN6_A86DiagnosticoComplemento, IMSSOFFLIN6_n86DiagnosticoComplemento, IMSSOFFLIN6_A87DiagnosticoResumen, IMSSOFFLIN6_n87DiagnosticoResumen, IMSSOFFLIN6_A103DiagnosticoFechaAlta, IMSSOFFLIN6_n103DiagnosticoFechaAlta, IMSSOFFLIN6_A85DiagnosticoFechaIngreso, IMSSOFFLIN6_n85DiagnosticoFechaIngreso,
            IMSSOFFLIN6_A1CIE10Id, IMSSOFFLIN6_A3PacienteAgregado, IMSSOFFLIN6_A2PacienteNSS
            }
            , new Object[] {
            IMSSOFFLIN7_A314nada, IMSSOFFLIN7_A302TextoDescripcion, IMSSOFFLIN7_A301TextoTitulo, IMSSOFFLIN7_A67TextoId
            }
            , new Object[] {
            IMSSOFFLIN8_A133PacienteNSSAgregado, IMSSOFFLIN8_A40000DXAuxImagenImg_GXI, IMSSOFFLIN8_A84DXAuxImagenUserAlta, IMSSOFFLIN8_A83DXAuxImagenFechaAlta, IMSSOFFLIN8_A82DXAuxImagenImg, IMSSOFFLIN8_A313DXAuxImagenExtension, IMSSOFFLIN8_A132DXAuxImagenNombre, IMSSOFFLIN8_A5DXAuxImagenId, IMSSOFFLIN8_A1CIE10Id, IMSSOFFLIN8_A3PacienteAgregado,
            IMSSOFFLIN8_A2PacienteNSS
            }
            , new Object[] {
            IMSSOFFLIN9_A133PacienteNSSAgregado, IMSSOFFLIN9_A79DXAuxDoctoNombre, IMSSOFFLIN9_A78DXAuxDoctoExtension, IMSSOFFLIN9_A81DXAuxDoctoUserAlta, IMSSOFFLIN9_A80DXAuxDoctoFechaAlta, IMSSOFFLIN9_A77DXAuxDoctoDocumento, IMSSOFFLIN9_A4DXAuxDoctoId, IMSSOFFLIN9_A1CIE10Id, IMSSOFFLIN9_A3PacienteAgregado, IMSSOFFLIN9_A2PacienteNSS
            }
            , new Object[] {
            IMSSOFFLIN10_A330ClavePresupuestal, IMSSOFFLIN10_A328IDEE, IMSSOFFLIN10_n328IDEE, IMSSOFFLIN10_A325CURP, IMSSOFFLIN10_n325CURP, IMSSOFFLIN10_A327DhUMF, IMSSOFFLIN10_n327DhUMF, IMSSOFFLIN10_A326DhDeleg, IMSSOFFLIN10_n326DhDeleg, IMSSOFFLIN10_A324Consultorio,
            IMSSOFFLIN10_n324Consultorio, IMSSOFFLIN10_A323ConDerechoSm, IMSSOFFLIN10_n323ConDerechoSm, IMSSOFFLIN10_A322ConDerechoInc, IMSSOFFLIN10_n322ConDerechoInc, IMSSOFFLIN10_A312PacienteServicioId, IMSSOFFLIN10_A130PacienteCie10Id, IMSSOFFLIN10_A133PacienteNSSAgregado, IMSSOFFLIN10_A131PacienteCama, IMSSOFFLIN10_A287PacienteDiagnosticoPhone,
            IMSSOFFLIN10_A129PacienteDiagnosticoResumido, IMSSOFFLIN10_A128PacienteDiagnostico, IMSSOFFLIN10_A134PAcienteFechaIngreso, IMSSOFFLIN10_A124PacienteNombreCompleto, IMSSOFFLIN10_A123PacienteReferencia, IMSSOFFLIN10_n123PacienteReferencia, IMSSOFFLIN10_A122PacienteFamiliar, IMSSOFFLIN10_n122PacienteFamiliar, IMSSOFFLIN10_A121PacienteTelefono, IMSSOFFLIN10_n121PacienteTelefono,
            IMSSOFFLIN10_A120PacienteGenero, IMSSOFFLIN10_n120PacienteGenero, IMSSOFFLIN10_A118PacienteEdad, IMSSOFFLIN10_A119PacienteFechaNacimiento, IMSSOFFLIN10_A114PacienteApMat, IMSSOFFLIN10_n114PacienteApMat, IMSSOFFLIN10_A113PacienteApPat, IMSSOFFLIN10_A112PacienteNombre, IMSSOFFLIN10_A3PacienteAgregado, IMSSOFFLIN10_A2PacienteNSS
            }
            , new Object[] {
            IMSSOFFLIN11_A297ExtensionNombre, IMSSOFFLIN11_A296ExtensionTipo, IMSSOFFLIN11_A66ExtensionId
            }
            , new Object[] {
            IMSSOFFLIN12_A136FormatoPacienteMedicoMatricula, IMSSOFFLIN12_A137FormatoPacienteMedicoNombre, IMSSOFFLIN12_A9DFFormInstId, IMSSOFFLIN12_A63FormatoPacienteAgregado, IMSSOFFLIN12_A62FormatoPacienteNSS
            }
            , new Object[] {
            IMSSOFFLIN13_A304DFElemFormReq, IMSSOFFLIN13_A299DFElemFormLoadRule, IMSSOFFLIN13_n299DFElemFormLoadRule, IMSSOFFLIN13_A263DFElemFormMetadata, IMSSOFFLIN13_n263DFElemFormMetadata, IMSSOFFLIN13_A264DFElemFormShwNbr, IMSSOFFLIN13_n264DFElemFormShwNbr, IMSSOFFLIN13_A262DFElemFormDateSel, IMSSOFFLIN13_n262DFElemFormDateSel, IMSSOFFLIN13_A259DFElemFormHasPmpt,
            IMSSOFFLIN13_n259DFElemFormHasPmpt, IMSSOFFLIN13_A184DFElemFormIsFlt, IMSSOFFLIN13_n184DFElemFormIsFlt, IMSSOFFLIN13_A183DFElemFormCmpWth, IMSSOFFLIN13_n183DFElemFormCmpWth, IMSSOFFLIN13_A182DFElemFormLblWth, IMSSOFFLIN13_n182DFElemFormLblWth, IMSSOFFLIN13_A307DFElemFormPrtPic, IMSSOFFLIN13_A282DFElemFormPrtShwNbr, IMSSOFFLIN13_A281DFElemFormPrtNumColSkip,
            IMSSOFFLIN13_A273DFElemFormPrtNumRowSkip, IMSSOFFLIN13_A271DFElemFormPrtAddRows, IMSSOFFLIN13_A270DFElemFormPrtName, IMSSOFFLIN13_A191DFElemFormIsVisPrt, IMSSOFFLIN13_A190DFElemFormIsVis, IMSSOFFLIN13_A189DFElemFormIsColap, IMSSOFFLIN13_A188DFElemFormAllowIns, IMSSOFFLIN13_n188DFElemFormAllowIns, IMSSOFFLIN13_A187DFElemFormAllowUpd, IMSSOFFLIN13_n187DFElemFormAllowUpd,
            IMSSOFFLIN13_A186DFElemFormAllowDlt, IMSSOFFLIN13_n186DFElemFormAllowDlt, IMSSOFFLIN13_A181DFElemFormInhType, IMSSOFFLIN13_A36DFElemFormPos, IMSSOFFLIN13_A185DFElemFormName, IMSSOFFLIN13_A19DFElemVer, IMSSOFFLIN13_A18DFElemId, IMSSOFFLIN13_A12DFFormVer, IMSSOFFLIN13_A11DFFormId
            }
            , new Object[] {
            IMSSOFFLIN14_A145DFElemFormInstFileName, IMSSOFFLIN14_n145DFElemFormInstFileName, IMSSOFFLIN14_A144DFElemFormInstFileType, IMSSOFFLIN14_n144DFElemFormInstFileType, IMSSOFFLIN14_A143DFElemFormInstBlob, IMSSOFFLIN14_n143DFElemFormInstBlob, IMSSOFFLIN14_A141DFElemFormInstVal, IMSSOFFLIN14_n141DFElemFormInstVal, IMSSOFFLIN14_A19DFElemVer, IMSSOFFLIN14_A18DFElemId,
            IMSSOFFLIN14_A9DFFormInstId
            }
            , new Object[] {
            IMSSOFFLIN15_A148DFElemFormInstSubElemFileName, IMSSOFFLIN15_n148DFElemFormInstSubElemFileName, IMSSOFFLIN15_A147DFElemFormInstSubElemFileType, IMSSOFFLIN15_n147DFElemFormInstSubElemFileType, IMSSOFFLIN15_A37DFSubElemFormElemId, IMSSOFFLIN15_A38DFSubElemFormElemVer, IMSSOFFLIN15_A69DFElemFormInstSubElemRow, IMSSOFFLIN15_A142DFElemFormInstSubElemVal, IMSSOFFLIN15_n142DFElemFormInstSubElemVal, IMSSOFFLIN15_A146DFElemFormInstSubElemBlob,
            IMSSOFFLIN15_n146DFElemFormInstSubElemBlob, IMSSOFFLIN15_A68DFElemFormInstSubElemId, IMSSOFFLIN15_A19DFElemVer, IMSSOFFLIN15_A18DFElemId, IMSSOFFLIN15_A9DFFormInstId
            }
            , new Object[] {
            IMSSOFFLIN16_A284DFTempOutFm, IMSSOFFLIN16_A278DFTempAddParmPrgName, IMSSOFFLIN16_A277DFTempBlob, IMSSOFFLIN16_A286DFTempFm, IMSSOFFLIN16_A283DFTempDsc, IMSSOFFLIN16_A55DFTempName, IMSSOFFLIN16_A12DFFormVer, IMSSOFFLIN16_A11DFFormId
            }
            , new Object[] {
            IMSSOFFLIN17_A298DFFormIsSD, IMSSOFFLIN17_A157DFFormRunDLT, IMSSOFFLIN17_A233DFFormHelpURL, IMSSOFFLIN17_A173DFFormPrefix, IMSSOFFLIN17_A232DFFormPmtHgh, IMSSOFFLIN17_n232DFFormPmtHgh, IMSSOFFLIN17_A231DFFormPmtWth, IMSSOFFLIN17_n231DFFormPmtWth, IMSSOFFLIN17_A234DFFormAct, IMSSOFFLIN17_A308DFFormDsc,
            IMSSOFFLIN17_A31DFFormName, IMSSOFFLIN17_A30DFFormGuid, IMSSOFFLIN17_A12DFFormVer, IMSSOFFLIN17_A11DFFormId
            }
            , new Object[] {
            IMSSOFFLIN18_A222DFDomStaValOptDsc, IMSSOFFLIN18_A34DFDomStaValOptOrd, IMSSOFFLIN18_A33DFDomStaValOptCod, IMSSOFFLIN18_A32DFDomId
            }
            , new Object[] {
            IMSSOFFLIN19_A197DFFormInstSignedPDF, IMSSOFFLIN19_n197DFFormInstSignedPDF, IMSSOFFLIN19_A198DFFormInstSignedBy, IMSSOFFLIN19_n198DFFormInstSignedBy, IMSSOFFLIN19_A155DFFormInstDT, IMSSOFFLIN19_A29DFFormInstFormVer, IMSSOFFLIN19_A28DFFormInstFormId, IMSSOFFLIN19_A9DFFormInstId
            }
            , new Object[] {
            IMSSOFFLIN20_A305DFElemReq, IMSSOFFLIN20_A300DFElemLoadRule, IMSSOFFLIN20_n300DFElemLoadRule, IMSSOFFLIN20_A265DFElemMetadata, IMSSOFFLIN20_n265DFElemMetadata, IMSSOFFLIN20_A238DFElemIsColap, IMSSOFFLIN20_A306DFElemPrtPic, IMSSOFFLIN20_A280DFElemPrtShwNbr, IMSSOFFLIN20_A279DFElemPrtNumColSkip, IMSSOFFLIN20_A274DFElemPrtNumRowSkip,
            IMSSOFFLIN20_A272DFElemPrtAddRows, IMSSOFFLIN20_A269DFElemPrtName, IMSSOFFLIN20_A260DFElemIsVisPrt, IMSSOFFLIN20_A237DFElemIsVis, IMSSOFFLIN20_A257DFElemLblWth, IMSSOFFLIN20_n257DFElemLblWth, IMSSOFFLIN20_A243DFElemCmpWth, IMSSOFFLIN20_n243DFElemCmpWth, IMSSOFFLIN20_A242DFElemIsFlt, IMSSOFFLIN20_n242DFElemIsFlt,
            IMSSOFFLIN20_A256DFElemFileType, IMSSOFFLIN20_n256DFElemFileType, IMSSOFFLIN20_A254DFElemRegexVal, IMSSOFFLIN20_n254DFElemRegexVal, IMSSOFFLIN20_A253DFElemAllowDlt, IMSSOFFLIN20_n253DFElemAllowDlt, IMSSOFFLIN20_A252DFElemAllowUpd, IMSSOFFLIN20_n252DFElemAllowUpd, IMSSOFFLIN20_A251DFElemAllowIns, IMSSOFFLIN20_n251DFElemAllowIns,
            IMSSOFFLIN20_A250DFElemUseBtns, IMSSOFFLIN20_n250DFElemUseBtns, IMSSOFFLIN20_A249DFElemIsOrd, IMSSOFFLIN20_n249DFElemIsOrd, IMSSOFFLIN20_A248DFElemMaxSuggRes, IMSSOFFLIN20_n248DFElemMaxSuggRes, IMSSOFFLIN20_A247DFElemForceSuggSel, IMSSOFFLIN20_n247DFElemForceSuggSel, IMSSOFFLIN20_A246DFElemMinCntCharSugg, IMSSOFFLIN20_n246DFElemMinCntCharSugg,
            IMSSOFFLIN20_A258DFElemDscPrgName, IMSSOFFLIN20_A245DFElemLoadPrgName, IMSSOFFLIN20_n245DFElemLoadPrgName, IMSSOFFLIN20_A267DFElemBtnPos, IMSSOFFLIN20_n267DFElemBtnPos, IMSSOFFLIN20_A268DFElemShwNbrLbl, IMSSOFFLIN20_n268DFElemShwNbrLbl, IMSSOFFLIN20_A266DFElemShwNbr, IMSSOFFLIN20_n266DFElemShwNbr, IMSSOFFLIN20_A261DFElemDateSel,
            IMSSOFFLIN20_n261DFElemDateSel, IMSSOFFLIN20_A244DFElemHasPmpt, IMSSOFFLIN20_n244DFElemHasPmpt, IMSSOFFLIN20_A180DFElemDftVal, IMSSOFFLIN20_n180DFElemDftVal, IMSSOFFLIN20_A241DFElemCntCols, IMSSOFFLIN20_n241DFElemCntCols, IMSSOFFLIN20_A240DFElemCntRows, IMSSOFFLIN20_n240DFElemCntRows, IMSSOFFLIN20_A239DFElemCntDec,
            IMSSOFFLIN20_n239DFElemCntDec, IMSSOFFLIN20_A255DFElemWth, IMSSOFFLIN20_n255DFElemWth, IMSSOFFLIN20_A236DFElemLen, IMSSOFFLIN20_n236DFElemLen, IMSSOFFLIN20_A196DFElemDsp, IMSSOFFLIN20_n196DFElemDsp, IMSSOFFLIN20_A178DFElemType, IMSSOFFLIN20_A32DFDomId, IMSSOFFLIN20_n32DFDomId,
            IMSSOFFLIN20_A192DFElemClsName, IMSSOFFLIN20_n192DFElemClsName, IMSSOFFLIN20_A235DFElemDsc, IMSSOFFLIN20_n235DFElemDsc, IMSSOFFLIN20_A149DFElemName, IMSSOFFLIN20_A35DFElemGuid, IMSSOFFLIN20_A19DFElemVer, IMSSOFFLIN20_A18DFElemId
            }
            , new Object[] {
            IMSSOFFLIN21_A71cveEspecialidad, IMSSOFFLIN21_A12DFFormVer, IMSSOFFLIN21_A11DFFormId
            }
            , new Object[] {
            IMSSOFFLIN22_A348PXDXFechaAsignacion, IMSSOFFLIN22_A347OcaSer, IMSSOFFLIN22_A346TpoDX, IMSSOFFLIN22_A345DX, IMSSOFFLIN22_A353IDEEPaciente
            }
            , new Object[] {
            IMSSOFFLIN23_A310DFDomPrtDsc, IMSSOFFLIN23_n310DFDomPrtDsc, IMSSOFFLIN23_A223DFDomLblWth, IMSSOFFLIN23_n223DFDomLblWth, IMSSOFFLIN23_A219DFDomCmpWth, IMSSOFFLIN23_n219DFDomCmpWth, IMSSOFFLIN23_A218DFDomIsFlt, IMSSOFFLIN23_n218DFDomIsFlt, IMSSOFFLIN23_A221DFDomFileType, IMSSOFFLIN23_n221DFDomFileType,
            IMSSOFFLIN23_A217DFDomRegexVal, IMSSOFFLIN23_A213DFDomAllowDlt, IMSSOFFLIN23_n213DFDomAllowDlt, IMSSOFFLIN23_A212DFDomAllowUpd, IMSSOFFLIN23_n212DFDomAllowUpd, IMSSOFFLIN23_A211DFDomAllowIns, IMSSOFFLIN23_n211DFDomAllowIns, IMSSOFFLIN23_A210DFDomUseBtns, IMSSOFFLIN23_n210DFDomUseBtns, IMSSOFFLIN23_A209DFDomIsOrd,
            IMSSOFFLIN23_n209DFDomIsOrd, IMSSOFFLIN23_A207DFDomMaxSuggRes, IMSSOFFLIN23_n207DFDomMaxSuggRes, IMSSOFFLIN23_A206DFDomForceSuggSel, IMSSOFFLIN23_n206DFDomForceSuggSel, IMSSOFFLIN23_A205DFDomMinCntCharSugg, IMSSOFFLIN23_n205DFDomMinCntCharSugg, IMSSOFFLIN23_A208DFDomDftVal, IMSSOFFLIN23_n208DFDomDftVal, IMSSOFFLIN23_A216DFDomCntCols,
            IMSSOFFLIN23_A215DFDomCntRows, IMSSOFFLIN23_A214DFDomCntDec, IMSSOFFLIN23_A220DFDomWth, IMSSOFFLIN23_A204DFDomLen, IMSSOFFLIN23_A195DFDomDsp, IMSSOFFLIN23_n195DFDomDsp, IMSSOFFLIN23_A194DFDomType, IMSSOFFLIN23_A224DFDomGUID, IMSSOFFLIN23_A203DFDomDsc, IMSSOFFLIN23_A32DFDomId
            }
            , new Object[] {
            IMSSOFFLIN24_A14DFFormRstVal, IMSSOFFLIN24_A13DFFormRstId, IMSSOFFLIN24_A12DFFormVer, IMSSOFFLIN24_A11DFFormId
            }
            , new Object[] {
            IMSSOFFLIN25_A164DFUserRstPwdIni, IMSSOFFLIN25_A24DFUserRstVal, IMSSOFFLIN25_A23DFUserRstId, IMSSOFFLIN25_A22DFUserExtId
            }
            , new Object[] {
            IMSSOFFLIN26_A39DFSubElemFormPos, IMSSOFFLIN26_n39DFSubElemFormPos, IMSSOFFLIN26_A38DFSubElemFormElemVer, IMSSOFFLIN26_A37DFSubElemFormElemId, IMSSOFFLIN26_A19DFElemVer, IMSSOFFLIN26_A18DFElemId, IMSSOFFLIN26_A12DFFormVer, IMSSOFFLIN26_A11DFFormId
            }
            , new Object[] {
            IMSSOFFLIN27_A42DFFilElemFormElemVer, IMSSOFFLIN27_A41DFFilElemFormElemId, IMSSOFFLIN27_A43DFFilElemFormPos, IMSSOFFLIN27_A40DFFilElemFormId, IMSSOFFLIN27_A19DFElemVer, IMSSOFFLIN27_A18DFElemId, IMSSOFFLIN27_A12DFFormVer, IMSSOFFLIN27_A11DFFormId
            }
            , new Object[] {
            IMSSOFFLIN28_A7HospitalId, IMSSOFFLIN28_n7HospitalId, IMSSOFFLIN28_A104ServicioDescripcion, IMSSOFFLIN28_A6ServicioId
            }
            , new Object[] {
            IMSSOFFLIN29_A12DFFormVer, IMSSOFFLIN29_A11DFFormId, IMSSOFFLIN29_A321fecBajaEspecialidad, IMSSOFFLIN29_n321fecBajaEspecialidad, IMSSOFFLIN29_A320desEspecialidad, IMSSOFFLIN29_A71cveEspecialidad
            }
            , new Object[] {
            IMSSOFFLIN30_A28DFFormInstFormId, IMSSOFFLIN30_A139DFUplFileExt, IMSSOFFLIN30_A140DFUplFileName, IMSSOFFLIN30_A138DFUplFile, IMSSOFFLIN30_A10DFUplKey, IMSSOFFLIN30_A9DFFormInstId
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
   protected short A102MMatricula ;
   protected short A101MApMat ;
   protected short A100MApPat ;
   protected short A99MNombre ;
   protected short A98MBMatricula ;
   protected short A94JSMatricula ;
   protected short A6ServicioId ;
   protected short A314nada ;
   protected short A67TextoId ;
   protected short A5DXAuxImagenId ;
   protected short A4DXAuxDoctoId ;
   protected short A312PacienteServicioId ;
   protected short A118PacienteEdad ;
   protected short A296ExtensionTipo ;
   protected short A66ExtensionId ;
   protected short A347OcaSer ;
   protected short A346TpoDX ;
   protected short A43DFFilElemFormPos ;
   protected short A7HospitalId ;
   protected short GXv_int8[] ;
   protected short Gx_err ;
   protected int A25DFParmId ;
   protected int A1CIE10Id ;
   protected int A130PacienteCie10Id ;
   protected int A281DFElemFormPrtNumColSkip ;
   protected int A273DFElemFormPrtNumRowSkip ;
   protected int A36DFElemFormPos ;
   protected int A19DFElemVer ;
   protected int A18DFElemId ;
   protected int A12DFFormVer ;
   protected int A11DFFormId ;
   protected int A37DFSubElemFormElemId ;
   protected int A38DFSubElemFormElemVer ;
   protected int A69DFElemFormInstSubElemRow ;
   protected int A68DFElemFormInstSubElemId ;
   protected int A232DFFormPmtHgh ;
   protected int A231DFFormPmtWth ;
   protected int A34DFDomStaValOptOrd ;
   protected int A32DFDomId ;
   protected int A29DFFormInstFormVer ;
   protected int A28DFFormInstFormId ;
   protected int A279DFElemPrtNumColSkip ;
   protected int A274DFElemPrtNumRowSkip ;
   protected int A248DFElemMaxSuggRes ;
   protected int A246DFElemMinCntCharSugg ;
   protected int A241DFElemCntCols ;
   protected int A240DFElemCntRows ;
   protected int A239DFElemCntDec ;
   protected int A255DFElemWth ;
   protected int A236DFElemLen ;
   protected int A345DX ;
   protected int A207DFDomMaxSuggRes ;
   protected int A205DFDomMinCntCharSugg ;
   protected int A216DFDomCntCols ;
   protected int A215DFDomCntRows ;
   protected int A214DFDomCntDec ;
   protected int A220DFDomWth ;
   protected int A204DFDomLen ;
   protected int A13DFFormRstId ;
   protected int A23DFUserRstId ;
   protected int A39DFSubElemFormPos ;
   protected int A42DFFilElemFormElemVer ;
   protected int A41DFFilElemFormElemId ;
   protected int A40DFFilElemFormId ;
   protected long A65MedMatricula ;
   protected long GXV1 ;
   protected long A9DFFormInstId ;
   protected long A136FormatoPacienteMedicoMatricula ;
   protected String AV4Matricula ;
   protected String AV5UserMedico ;
   protected String GXt_char1 ;
   protected String GXv_char2[] ;
   protected String scmdbuf ;
   protected String A340MedCedProf ;
   protected String A291MedApMat ;
   protected String A290MedApPat ;
   protected String A288MedNom ;
   protected String A64UserMed ;
   protected String gxlinehash ;
   protected String gxtabledata ;
   protected String gxtablecurrenthash ;
   protected String gxtablestoredhash ;
   protected String gxdeviceidentifier ;
   protected String A8Matricula ;
   protected String A3PacienteAgregado ;
   protected String A2PacienteNSS ;
   protected String A166DFParmVal ;
   protected String A165DFParmName ;
   protected String A97MBApMat ;
   protected String A96MBApPat ;
   protected String A95MBNombre ;
   protected String A93JSApMat ;
   protected String A92JSApPat ;
   protected String A91JSNombre ;
   protected String A88Cama ;
   protected String A84DXAuxImagenUserAlta ;
   protected String A313DXAuxImagenExtension ;
   protected String A132DXAuxImagenNombre ;
   protected String A79DXAuxDoctoNombre ;
   protected String A78DXAuxDoctoExtension ;
   protected String A81DXAuxDoctoUserAlta ;
   protected String A330ClavePresupuestal ;
   protected String A328IDEE ;
   protected String A325CURP ;
   protected String A327DhUMF ;
   protected String A326DhDeleg ;
   protected String A324Consultorio ;
   protected String A323ConDerechoSm ;
   protected String A322ConDerechoInc ;
   protected String A131PacienteCama ;
   protected String A124PacienteNombreCompleto ;
   protected String A123PacienteReferencia ;
   protected String A121PacienteTelefono ;
   protected String A120PacienteGenero ;
   protected String A114PacienteApMat ;
   protected String A113PacienteApPat ;
   protected String A112PacienteNombre ;
   protected String A297ExtensionNombre ;
   protected String A63FormatoPacienteAgregado ;
   protected String A62FormatoPacienteNSS ;
   protected String A184DFElemFormIsFlt ;
   protected String A183DFElemFormCmpWth ;
   protected String A182DFElemFormLblWth ;
   protected String A270DFElemFormPrtName ;
   protected String A181DFElemFormInhType ;
   protected String A185DFElemFormName ;
   protected String A145DFElemFormInstFileName ;
   protected String A144DFElemFormInstFileType ;
   protected String A148DFElemFormInstSubElemFileName ;
   protected String A147DFElemFormInstSubElemFileType ;
   protected String A284DFTempOutFm ;
   protected String A286DFTempFm ;
   protected String A55DFTempName ;
   protected String A31DFFormName ;
   protected String A222DFDomStaValOptDsc ;
   protected String A33DFDomStaValOptCod ;
   protected String A269DFElemPrtName ;
   protected String A257DFElemLblWth ;
   protected String A243DFElemCmpWth ;
   protected String A242DFElemIsFlt ;
   protected String A256DFElemFileType ;
   protected String A254DFElemRegexVal ;
   protected String A267DFElemBtnPos ;
   protected String A268DFElemShwNbrLbl ;
   protected String A180DFElemDftVal ;
   protected String A196DFElemDsp ;
   protected String A178DFElemType ;
   protected String A192DFElemClsName ;
   protected String A149DFElemName ;
   protected String A71cveEspecialidad ;
   protected String A353IDEEPaciente ;
   protected String A223DFDomLblWth ;
   protected String A219DFDomCmpWth ;
   protected String A218DFDomIsFlt ;
   protected String A221DFDomFileType ;
   protected String A217DFDomRegexVal ;
   protected String A208DFDomDftVal ;
   protected String A195DFDomDsp ;
   protected String A194DFDomType ;
   protected String A203DFDomDsc ;
   protected String A14DFFormRstVal ;
   protected String A24DFUserRstVal ;
   protected String A104ServicioDescripcion ;
   protected String A139DFUplFileExt ;
   protected String A140DFUplFileName ;
   protected String A10DFUplKey ;
   protected String gxsourcever ;
   protected String DEVICEID ;
   protected String QUERYID ;
   protected String RESULTSET ;
   protected java.util.Date A293MedUltAct ;
   protected java.util.Date A90DiagnosticoCirugiaFecha ;
   protected java.util.Date A103DiagnosticoFechaAlta ;
   protected java.util.Date A83DXAuxImagenFechaAlta ;
   protected java.util.Date A80DXAuxDoctoFechaAlta ;
   protected java.util.Date A155DFFormInstDT ;
   protected java.util.Date A348PXDXFechaAsignacion ;
   protected java.util.Date A341FecBajaMed ;
   protected java.util.Date A85DiagnosticoFechaIngreso ;
   protected java.util.Date A134PAcienteFechaIngreso ;
   protected java.util.Date A119PacienteFechaNacimiento ;
   protected java.util.Date A321fecBajaEspecialidad ;
   protected boolean returnInSub ;
   protected boolean n341FecBajaMed ;
   protected boolean A303MedDebMosTerm ;
   protected boolean n303MedDebMosTerm ;
   protected boolean A295MedDebValDat ;
   protected boolean A167DFParmIsMetaData ;
   protected boolean n102MMatricula ;
   protected boolean n101MApMat ;
   protected boolean n100MApPat ;
   protected boolean n99MNombre ;
   protected boolean n98MBMatricula ;
   protected boolean n97MBApMat ;
   protected boolean n96MBApPat ;
   protected boolean n95MBNombre ;
   protected boolean n94JSMatricula ;
   protected boolean n93JSApMat ;
   protected boolean n92JSApPat ;
   protected boolean n91JSNombre ;
   protected boolean n90DiagnosticoCirugiaFecha ;
   protected boolean n89DiagnosticoCirugia ;
   protected boolean n88Cama ;
   protected boolean n86DiagnosticoComplemento ;
   protected boolean n87DiagnosticoResumen ;
   protected boolean n103DiagnosticoFechaAlta ;
   protected boolean n85DiagnosticoFechaIngreso ;
   protected boolean n328IDEE ;
   protected boolean n325CURP ;
   protected boolean n327DhUMF ;
   protected boolean n326DhDeleg ;
   protected boolean n324Consultorio ;
   protected boolean n323ConDerechoSm ;
   protected boolean n322ConDerechoInc ;
   protected boolean n123PacienteReferencia ;
   protected boolean n122PacienteFamiliar ;
   protected boolean n121PacienteTelefono ;
   protected boolean n120PacienteGenero ;
   protected boolean n114PacienteApMat ;
   protected boolean A304DFElemFormReq ;
   protected boolean n299DFElemFormLoadRule ;
   protected boolean n263DFElemFormMetadata ;
   protected boolean A264DFElemFormShwNbr ;
   protected boolean n264DFElemFormShwNbr ;
   protected boolean A262DFElemFormDateSel ;
   protected boolean n262DFElemFormDateSel ;
   protected boolean A259DFElemFormHasPmpt ;
   protected boolean n259DFElemFormHasPmpt ;
   protected boolean n184DFElemFormIsFlt ;
   protected boolean n183DFElemFormCmpWth ;
   protected boolean n182DFElemFormLblWth ;
   protected boolean A282DFElemFormPrtShwNbr ;
   protected boolean A271DFElemFormPrtAddRows ;
   protected boolean A191DFElemFormIsVisPrt ;
   protected boolean A190DFElemFormIsVis ;
   protected boolean A189DFElemFormIsColap ;
   protected boolean A188DFElemFormAllowIns ;
   protected boolean n188DFElemFormAllowIns ;
   protected boolean A187DFElemFormAllowUpd ;
   protected boolean n187DFElemFormAllowUpd ;
   protected boolean A186DFElemFormAllowDlt ;
   protected boolean n186DFElemFormAllowDlt ;
   protected boolean n145DFElemFormInstFileName ;
   protected boolean n144DFElemFormInstFileType ;
   protected boolean n143DFElemFormInstBlob ;
   protected boolean n141DFElemFormInstVal ;
   protected boolean n148DFElemFormInstSubElemFileName ;
   protected boolean n147DFElemFormInstSubElemFileType ;
   protected boolean n142DFElemFormInstSubElemVal ;
   protected boolean n146DFElemFormInstSubElemBlob ;
   protected boolean A298DFFormIsSD ;
   protected boolean A157DFFormRunDLT ;
   protected boolean n232DFFormPmtHgh ;
   protected boolean n231DFFormPmtWth ;
   protected boolean A234DFFormAct ;
   protected boolean n32DFDomId ;
   protected boolean n197DFFormInstSignedPDF ;
   protected boolean n198DFFormInstSignedBy ;
   protected boolean A305DFElemReq ;
   protected boolean n300DFElemLoadRule ;
   protected boolean n265DFElemMetadata ;
   protected boolean A238DFElemIsColap ;
   protected boolean A280DFElemPrtShwNbr ;
   protected boolean A272DFElemPrtAddRows ;
   protected boolean A260DFElemIsVisPrt ;
   protected boolean A237DFElemIsVis ;
   protected boolean n257DFElemLblWth ;
   protected boolean n243DFElemCmpWth ;
   protected boolean n242DFElemIsFlt ;
   protected boolean n256DFElemFileType ;
   protected boolean n254DFElemRegexVal ;
   protected boolean A253DFElemAllowDlt ;
   protected boolean n253DFElemAllowDlt ;
   protected boolean A252DFElemAllowUpd ;
   protected boolean n252DFElemAllowUpd ;
   protected boolean A251DFElemAllowIns ;
   protected boolean n251DFElemAllowIns ;
   protected boolean A250DFElemUseBtns ;
   protected boolean n250DFElemUseBtns ;
   protected boolean A249DFElemIsOrd ;
   protected boolean n249DFElemIsOrd ;
   protected boolean n248DFElemMaxSuggRes ;
   protected boolean A247DFElemForceSuggSel ;
   protected boolean n247DFElemForceSuggSel ;
   protected boolean n246DFElemMinCntCharSugg ;
   protected boolean n245DFElemLoadPrgName ;
   protected boolean n267DFElemBtnPos ;
   protected boolean n268DFElemShwNbrLbl ;
   protected boolean A266DFElemShwNbr ;
   protected boolean n266DFElemShwNbr ;
   protected boolean A261DFElemDateSel ;
   protected boolean n261DFElemDateSel ;
   protected boolean A244DFElemHasPmpt ;
   protected boolean n244DFElemHasPmpt ;
   protected boolean n180DFElemDftVal ;
   protected boolean n241DFElemCntCols ;
   protected boolean n240DFElemCntRows ;
   protected boolean n239DFElemCntDec ;
   protected boolean n255DFElemWth ;
   protected boolean n236DFElemLen ;
   protected boolean n196DFElemDsp ;
   protected boolean n192DFElemClsName ;
   protected boolean n235DFElemDsc ;
   protected boolean A310DFDomPrtDsc ;
   protected boolean n310DFDomPrtDsc ;
   protected boolean n223DFDomLblWth ;
   protected boolean n219DFDomCmpWth ;
   protected boolean n218DFDomIsFlt ;
   protected boolean n221DFDomFileType ;
   protected boolean A213DFDomAllowDlt ;
   protected boolean n213DFDomAllowDlt ;
   protected boolean A212DFDomAllowUpd ;
   protected boolean n212DFDomAllowUpd ;
   protected boolean A211DFDomAllowIns ;
   protected boolean n211DFDomAllowIns ;
   protected boolean A210DFDomUseBtns ;
   protected boolean n210DFDomUseBtns ;
   protected boolean A209DFDomIsOrd ;
   protected boolean n209DFDomIsOrd ;
   protected boolean n207DFDomMaxSuggRes ;
   protected boolean A206DFDomForceSuggSel ;
   protected boolean n206DFDomForceSuggSel ;
   protected boolean n205DFDomMinCntCharSugg ;
   protected boolean n208DFDomDftVal ;
   protected boolean n195DFDomDsp ;
   protected boolean A164DFUserRstPwdIni ;
   protected boolean n39DFSubElemFormPos ;
   protected boolean n7HospitalId ;
   protected boolean n321fecBajaEspecialidad ;
   protected String A89DiagnosticoCirugia ;
   protected String A86DiagnosticoComplemento ;
   protected String A87DiagnosticoResumen ;
   protected String A302TextoDescripcion ;
   protected String A77DXAuxDoctoDocumento ;
   protected String A143DFElemFormInstBlob ;
   protected String A146DFElemFormInstSubElemBlob ;
   protected String A277DFTempBlob ;
   protected String A197DFFormInstSignedPDF ;
   protected String A138DFUplFile ;
   protected String A133PacienteNSSAgregado ;
   protected String A76CIE10Descripcion ;
   protected String A127CIECodigo ;
   protected String A301TextoTitulo ;
   protected String A40000DXAuxImagenImg_GXI ;
   protected String A287PacienteDiagnosticoPhone ;
   protected String A129PacienteDiagnosticoResumido ;
   protected String A128PacienteDiagnostico ;
   protected String A122PacienteFamiliar ;
   protected String A137FormatoPacienteMedicoNombre ;
   protected String A299DFElemFormLoadRule ;
   protected String A263DFElemFormMetadata ;
   protected String A307DFElemFormPrtPic ;
   protected String A141DFElemFormInstVal ;
   protected String A142DFElemFormInstSubElemVal ;
   protected String A278DFTempAddParmPrgName ;
   protected String A283DFTempDsc ;
   protected String A233DFFormHelpURL ;
   protected String A173DFFormPrefix ;
   protected String A308DFFormDsc ;
   protected String A198DFFormInstSignedBy ;
   protected String A300DFElemLoadRule ;
   protected String A265DFElemMetadata ;
   protected String A306DFElemPrtPic ;
   protected String A258DFElemDscPrgName ;
   protected String A245DFElemLoadPrgName ;
   protected String A235DFElemDsc ;
   protected String A22DFUserExtId ;
   protected String A320desEspecialidad ;
   protected String A82DXAuxImagenImg ;
   protected java.util.UUID A30DFFormGuid ;
   protected java.util.UUID A35DFElemGuid ;
   protected java.util.UUID A224DFDomGUID ;
   protected com.genexus.internet.HttpRequest gxhttpr ;
   protected com.genexus.internet.StringCollection gxsyncheader ;
   protected com.genexus.internet.StringCollection gxsyncline ;
   protected com.genexus.internet.StringCollection gxtablemdata ;
   protected com.genexus.internet.StringCollection gxsynchashkey ;
   protected com.genexus.internet.StringCollection gxsetline ;
   protected com.genexus.internet.StringCollection gxsyncheaderpre ;
   protected com.genexus.internet.StringCollection gxsyncline_hash ;
   protected com.genexus.internet.StringCollection gxsyncheaderline ;
   protected com.genexus.GxUnknownObjectCollection gxsyncresponse ;
   protected com.genexus.GxUnknownObjectCollection gxfinalsync ;
   protected com.genexus.GxUnknownObjectCollection gxsynchashset ;
   protected com.genexus.GxUnknownObjectCollection gxsyncvalueset ;
   protected com.genexus.GxUnknownObjectCollection gxsetvalueline ;
   protected com.genexus.GxUnknownObjectCollection gxsyncinsert ;
   protected com.genexus.GxUnknownObjectCollection gxsyncupdate ;
   protected com.genexus.GxUnknownObjectCollection gxsyncdelete ;
   protected com.genexus.GxUnknownObjectCollection gxtablehashlist ;
   protected com.genexus.GxUnknownObjectCollection gxsyncresponse_hash ;
   protected com.genexus.GxUnknownObjectCollection GXv_objcol_gxjsonable7[] ;
   protected com.genexus.GxUnknownObjectCollection GXv_objcol_gxjsonable6[] ;
   protected com.genexus.GxUnknownObjectCollection GXv_objcol_gxjsonable5[] ;
   protected com.genexus.GxUnknownObjectCollection gxallsyncresponse ;
   protected com.genexus.GxUnknownObjectCollection gxtableheadlist ;
   protected IDataStoreProvider pr_default ;
   protected java.util.Date[] IMSSOFFLIN2_A341FecBajaMed ;
   protected boolean[] IMSSOFFLIN2_n341FecBajaMed ;
   protected boolean[] IMSSOFFLIN2_A303MedDebMosTerm ;
   protected boolean[] IMSSOFFLIN2_n303MedDebMosTerm ;
   protected boolean[] IMSSOFFLIN2_A295MedDebValDat ;
   protected java.util.Date[] IMSSOFFLIN2_A293MedUltAct ;
   protected String[] IMSSOFFLIN2_A340MedCedProf ;
   protected String[] IMSSOFFLIN2_A291MedApMat ;
   protected String[] IMSSOFFLIN2_A290MedApPat ;
   protected String[] IMSSOFFLIN2_A288MedNom ;
   protected String[] IMSSOFFLIN2_A64UserMed ;
   protected long[] IMSSOFFLIN2_A65MedMatricula ;
   protected String[] IMSSOFFLIN3_A133PacienteNSSAgregado ;
   protected String[] IMSSOFFLIN3_A8Matricula ;
   protected String[] IMSSOFFLIN3_A3PacienteAgregado ;
   protected String[] IMSSOFFLIN3_A2PacienteNSS ;
   protected boolean[] IMSSOFFLIN4_A167DFParmIsMetaData ;
   protected String[] IMSSOFFLIN4_A166DFParmVal ;
   protected String[] IMSSOFFLIN4_A165DFParmName ;
   protected int[] IMSSOFFLIN4_A25DFParmId ;
   protected String[] IMSSOFFLIN5_A76CIE10Descripcion ;
   protected String[] IMSSOFFLIN5_A127CIECodigo ;
   protected int[] IMSSOFFLIN5_A1CIE10Id ;
   protected String[] IMSSOFFLIN6_A133PacienteNSSAgregado ;
   protected short[] IMSSOFFLIN6_A102MMatricula ;
   protected boolean[] IMSSOFFLIN6_n102MMatricula ;
   protected short[] IMSSOFFLIN6_A101MApMat ;
   protected boolean[] IMSSOFFLIN6_n101MApMat ;
   protected short[] IMSSOFFLIN6_A100MApPat ;
   protected boolean[] IMSSOFFLIN6_n100MApPat ;
   protected short[] IMSSOFFLIN6_A99MNombre ;
   protected boolean[] IMSSOFFLIN6_n99MNombre ;
   protected short[] IMSSOFFLIN6_A98MBMatricula ;
   protected boolean[] IMSSOFFLIN6_n98MBMatricula ;
   protected String[] IMSSOFFLIN6_A97MBApMat ;
   protected boolean[] IMSSOFFLIN6_n97MBApMat ;
   protected String[] IMSSOFFLIN6_A96MBApPat ;
   protected boolean[] IMSSOFFLIN6_n96MBApPat ;
   protected String[] IMSSOFFLIN6_A95MBNombre ;
   protected boolean[] IMSSOFFLIN6_n95MBNombre ;
   protected short[] IMSSOFFLIN6_A94JSMatricula ;
   protected boolean[] IMSSOFFLIN6_n94JSMatricula ;
   protected String[] IMSSOFFLIN6_A93JSApMat ;
   protected boolean[] IMSSOFFLIN6_n93JSApMat ;
   protected String[] IMSSOFFLIN6_A92JSApPat ;
   protected boolean[] IMSSOFFLIN6_n92JSApPat ;
   protected String[] IMSSOFFLIN6_A91JSNombre ;
   protected boolean[] IMSSOFFLIN6_n91JSNombre ;
   protected java.util.Date[] IMSSOFFLIN6_A90DiagnosticoCirugiaFecha ;
   protected boolean[] IMSSOFFLIN6_n90DiagnosticoCirugiaFecha ;
   protected String[] IMSSOFFLIN6_A89DiagnosticoCirugia ;
   protected boolean[] IMSSOFFLIN6_n89DiagnosticoCirugia ;
   protected String[] IMSSOFFLIN6_A88Cama ;
   protected boolean[] IMSSOFFLIN6_n88Cama ;
   protected short[] IMSSOFFLIN6_A6ServicioId ;
   protected String[] IMSSOFFLIN6_A86DiagnosticoComplemento ;
   protected boolean[] IMSSOFFLIN6_n86DiagnosticoComplemento ;
   protected String[] IMSSOFFLIN6_A87DiagnosticoResumen ;
   protected boolean[] IMSSOFFLIN6_n87DiagnosticoResumen ;
   protected java.util.Date[] IMSSOFFLIN6_A103DiagnosticoFechaAlta ;
   protected boolean[] IMSSOFFLIN6_n103DiagnosticoFechaAlta ;
   protected java.util.Date[] IMSSOFFLIN6_A85DiagnosticoFechaIngreso ;
   protected boolean[] IMSSOFFLIN6_n85DiagnosticoFechaIngreso ;
   protected int[] IMSSOFFLIN6_A1CIE10Id ;
   protected String[] IMSSOFFLIN6_A3PacienteAgregado ;
   protected String[] IMSSOFFLIN6_A2PacienteNSS ;
   protected short[] IMSSOFFLIN7_A314nada ;
   protected String[] IMSSOFFLIN7_A302TextoDescripcion ;
   protected String[] IMSSOFFLIN7_A301TextoTitulo ;
   protected short[] IMSSOFFLIN7_A67TextoId ;
   protected String[] IMSSOFFLIN8_A133PacienteNSSAgregado ;
   protected String[] IMSSOFFLIN8_A40000DXAuxImagenImg_GXI ;
   protected String[] IMSSOFFLIN8_A84DXAuxImagenUserAlta ;
   protected java.util.Date[] IMSSOFFLIN8_A83DXAuxImagenFechaAlta ;
   protected String[] IMSSOFFLIN8_A82DXAuxImagenImg ;
   protected String[] IMSSOFFLIN8_A313DXAuxImagenExtension ;
   protected String[] IMSSOFFLIN8_A132DXAuxImagenNombre ;
   protected short[] IMSSOFFLIN8_A5DXAuxImagenId ;
   protected int[] IMSSOFFLIN8_A1CIE10Id ;
   protected String[] IMSSOFFLIN8_A3PacienteAgregado ;
   protected String[] IMSSOFFLIN8_A2PacienteNSS ;
   protected String[] IMSSOFFLIN9_A133PacienteNSSAgregado ;
   protected String[] IMSSOFFLIN9_A79DXAuxDoctoNombre ;
   protected String[] IMSSOFFLIN9_A78DXAuxDoctoExtension ;
   protected String[] IMSSOFFLIN9_A81DXAuxDoctoUserAlta ;
   protected java.util.Date[] IMSSOFFLIN9_A80DXAuxDoctoFechaAlta ;
   protected String[] IMSSOFFLIN9_A77DXAuxDoctoDocumento ;
   protected short[] IMSSOFFLIN9_A4DXAuxDoctoId ;
   protected int[] IMSSOFFLIN9_A1CIE10Id ;
   protected String[] IMSSOFFLIN9_A3PacienteAgregado ;
   protected String[] IMSSOFFLIN9_A2PacienteNSS ;
   protected String[] IMSSOFFLIN10_A330ClavePresupuestal ;
   protected String[] IMSSOFFLIN10_A328IDEE ;
   protected boolean[] IMSSOFFLIN10_n328IDEE ;
   protected String[] IMSSOFFLIN10_A325CURP ;
   protected boolean[] IMSSOFFLIN10_n325CURP ;
   protected String[] IMSSOFFLIN10_A327DhUMF ;
   protected boolean[] IMSSOFFLIN10_n327DhUMF ;
   protected String[] IMSSOFFLIN10_A326DhDeleg ;
   protected boolean[] IMSSOFFLIN10_n326DhDeleg ;
   protected String[] IMSSOFFLIN10_A324Consultorio ;
   protected boolean[] IMSSOFFLIN10_n324Consultorio ;
   protected String[] IMSSOFFLIN10_A323ConDerechoSm ;
   protected boolean[] IMSSOFFLIN10_n323ConDerechoSm ;
   protected String[] IMSSOFFLIN10_A322ConDerechoInc ;
   protected boolean[] IMSSOFFLIN10_n322ConDerechoInc ;
   protected short[] IMSSOFFLIN10_A312PacienteServicioId ;
   protected int[] IMSSOFFLIN10_A130PacienteCie10Id ;
   protected String[] IMSSOFFLIN10_A133PacienteNSSAgregado ;
   protected String[] IMSSOFFLIN10_A131PacienteCama ;
   protected String[] IMSSOFFLIN10_A287PacienteDiagnosticoPhone ;
   protected String[] IMSSOFFLIN10_A129PacienteDiagnosticoResumido ;
   protected String[] IMSSOFFLIN10_A128PacienteDiagnostico ;
   protected java.util.Date[] IMSSOFFLIN10_A134PAcienteFechaIngreso ;
   protected String[] IMSSOFFLIN10_A124PacienteNombreCompleto ;
   protected String[] IMSSOFFLIN10_A123PacienteReferencia ;
   protected boolean[] IMSSOFFLIN10_n123PacienteReferencia ;
   protected String[] IMSSOFFLIN10_A122PacienteFamiliar ;
   protected boolean[] IMSSOFFLIN10_n122PacienteFamiliar ;
   protected String[] IMSSOFFLIN10_A121PacienteTelefono ;
   protected boolean[] IMSSOFFLIN10_n121PacienteTelefono ;
   protected String[] IMSSOFFLIN10_A120PacienteGenero ;
   protected boolean[] IMSSOFFLIN10_n120PacienteGenero ;
   protected short[] IMSSOFFLIN10_A118PacienteEdad ;
   protected java.util.Date[] IMSSOFFLIN10_A119PacienteFechaNacimiento ;
   protected String[] IMSSOFFLIN10_A114PacienteApMat ;
   protected boolean[] IMSSOFFLIN10_n114PacienteApMat ;
   protected String[] IMSSOFFLIN10_A113PacienteApPat ;
   protected String[] IMSSOFFLIN10_A112PacienteNombre ;
   protected String[] IMSSOFFLIN10_A3PacienteAgregado ;
   protected String[] IMSSOFFLIN10_A2PacienteNSS ;
   protected String[] IMSSOFFLIN11_A297ExtensionNombre ;
   protected short[] IMSSOFFLIN11_A296ExtensionTipo ;
   protected short[] IMSSOFFLIN11_A66ExtensionId ;
   protected long[] IMSSOFFLIN12_A136FormatoPacienteMedicoMatricula ;
   protected String[] IMSSOFFLIN12_A137FormatoPacienteMedicoNombre ;
   protected long[] IMSSOFFLIN12_A9DFFormInstId ;
   protected String[] IMSSOFFLIN12_A63FormatoPacienteAgregado ;
   protected String[] IMSSOFFLIN12_A62FormatoPacienteNSS ;
   protected boolean[] IMSSOFFLIN13_A304DFElemFormReq ;
   protected String[] IMSSOFFLIN13_A299DFElemFormLoadRule ;
   protected boolean[] IMSSOFFLIN13_n299DFElemFormLoadRule ;
   protected String[] IMSSOFFLIN13_A263DFElemFormMetadata ;
   protected boolean[] IMSSOFFLIN13_n263DFElemFormMetadata ;
   protected boolean[] IMSSOFFLIN13_A264DFElemFormShwNbr ;
   protected boolean[] IMSSOFFLIN13_n264DFElemFormShwNbr ;
   protected boolean[] IMSSOFFLIN13_A262DFElemFormDateSel ;
   protected boolean[] IMSSOFFLIN13_n262DFElemFormDateSel ;
   protected boolean[] IMSSOFFLIN13_A259DFElemFormHasPmpt ;
   protected boolean[] IMSSOFFLIN13_n259DFElemFormHasPmpt ;
   protected String[] IMSSOFFLIN13_A184DFElemFormIsFlt ;
   protected boolean[] IMSSOFFLIN13_n184DFElemFormIsFlt ;
   protected String[] IMSSOFFLIN13_A183DFElemFormCmpWth ;
   protected boolean[] IMSSOFFLIN13_n183DFElemFormCmpWth ;
   protected String[] IMSSOFFLIN13_A182DFElemFormLblWth ;
   protected boolean[] IMSSOFFLIN13_n182DFElemFormLblWth ;
   protected String[] IMSSOFFLIN13_A307DFElemFormPrtPic ;
   protected boolean[] IMSSOFFLIN13_A282DFElemFormPrtShwNbr ;
   protected int[] IMSSOFFLIN13_A281DFElemFormPrtNumColSkip ;
   protected int[] IMSSOFFLIN13_A273DFElemFormPrtNumRowSkip ;
   protected boolean[] IMSSOFFLIN13_A271DFElemFormPrtAddRows ;
   protected String[] IMSSOFFLIN13_A270DFElemFormPrtName ;
   protected boolean[] IMSSOFFLIN13_A191DFElemFormIsVisPrt ;
   protected boolean[] IMSSOFFLIN13_A190DFElemFormIsVis ;
   protected boolean[] IMSSOFFLIN13_A189DFElemFormIsColap ;
   protected boolean[] IMSSOFFLIN13_A188DFElemFormAllowIns ;
   protected boolean[] IMSSOFFLIN13_n188DFElemFormAllowIns ;
   protected boolean[] IMSSOFFLIN13_A187DFElemFormAllowUpd ;
   protected boolean[] IMSSOFFLIN13_n187DFElemFormAllowUpd ;
   protected boolean[] IMSSOFFLIN13_A186DFElemFormAllowDlt ;
   protected boolean[] IMSSOFFLIN13_n186DFElemFormAllowDlt ;
   protected String[] IMSSOFFLIN13_A181DFElemFormInhType ;
   protected int[] IMSSOFFLIN13_A36DFElemFormPos ;
   protected String[] IMSSOFFLIN13_A185DFElemFormName ;
   protected int[] IMSSOFFLIN13_A19DFElemVer ;
   protected int[] IMSSOFFLIN13_A18DFElemId ;
   protected int[] IMSSOFFLIN13_A12DFFormVer ;
   protected int[] IMSSOFFLIN13_A11DFFormId ;
   protected String[] IMSSOFFLIN14_A145DFElemFormInstFileName ;
   protected boolean[] IMSSOFFLIN14_n145DFElemFormInstFileName ;
   protected String[] IMSSOFFLIN14_A144DFElemFormInstFileType ;
   protected boolean[] IMSSOFFLIN14_n144DFElemFormInstFileType ;
   protected String[] IMSSOFFLIN14_A143DFElemFormInstBlob ;
   protected boolean[] IMSSOFFLIN14_n143DFElemFormInstBlob ;
   protected String[] IMSSOFFLIN14_A141DFElemFormInstVal ;
   protected boolean[] IMSSOFFLIN14_n141DFElemFormInstVal ;
   protected int[] IMSSOFFLIN14_A19DFElemVer ;
   protected int[] IMSSOFFLIN14_A18DFElemId ;
   protected long[] IMSSOFFLIN14_A9DFFormInstId ;
   protected String[] IMSSOFFLIN15_A148DFElemFormInstSubElemFileName ;
   protected boolean[] IMSSOFFLIN15_n148DFElemFormInstSubElemFileName ;
   protected String[] IMSSOFFLIN15_A147DFElemFormInstSubElemFileType ;
   protected boolean[] IMSSOFFLIN15_n147DFElemFormInstSubElemFileType ;
   protected int[] IMSSOFFLIN15_A37DFSubElemFormElemId ;
   protected int[] IMSSOFFLIN15_A38DFSubElemFormElemVer ;
   protected int[] IMSSOFFLIN15_A69DFElemFormInstSubElemRow ;
   protected String[] IMSSOFFLIN15_A142DFElemFormInstSubElemVal ;
   protected boolean[] IMSSOFFLIN15_n142DFElemFormInstSubElemVal ;
   protected String[] IMSSOFFLIN15_A146DFElemFormInstSubElemBlob ;
   protected boolean[] IMSSOFFLIN15_n146DFElemFormInstSubElemBlob ;
   protected int[] IMSSOFFLIN15_A68DFElemFormInstSubElemId ;
   protected int[] IMSSOFFLIN15_A19DFElemVer ;
   protected int[] IMSSOFFLIN15_A18DFElemId ;
   protected long[] IMSSOFFLIN15_A9DFFormInstId ;
   protected String[] IMSSOFFLIN16_A284DFTempOutFm ;
   protected String[] IMSSOFFLIN16_A278DFTempAddParmPrgName ;
   protected String[] IMSSOFFLIN16_A277DFTempBlob ;
   protected String[] IMSSOFFLIN16_A286DFTempFm ;
   protected String[] IMSSOFFLIN16_A283DFTempDsc ;
   protected String[] IMSSOFFLIN16_A55DFTempName ;
   protected int[] IMSSOFFLIN16_A12DFFormVer ;
   protected int[] IMSSOFFLIN16_A11DFFormId ;
   protected boolean[] IMSSOFFLIN17_A298DFFormIsSD ;
   protected boolean[] IMSSOFFLIN17_A157DFFormRunDLT ;
   protected String[] IMSSOFFLIN17_A233DFFormHelpURL ;
   protected String[] IMSSOFFLIN17_A173DFFormPrefix ;
   protected int[] IMSSOFFLIN17_A232DFFormPmtHgh ;
   protected boolean[] IMSSOFFLIN17_n232DFFormPmtHgh ;
   protected int[] IMSSOFFLIN17_A231DFFormPmtWth ;
   protected boolean[] IMSSOFFLIN17_n231DFFormPmtWth ;
   protected boolean[] IMSSOFFLIN17_A234DFFormAct ;
   protected String[] IMSSOFFLIN17_A308DFFormDsc ;
   protected String[] IMSSOFFLIN17_A31DFFormName ;
   protected java.util.UUID[] IMSSOFFLIN17_A30DFFormGuid ;
   protected int[] IMSSOFFLIN17_A12DFFormVer ;
   protected int[] IMSSOFFLIN17_A11DFFormId ;
   protected String[] IMSSOFFLIN18_A222DFDomStaValOptDsc ;
   protected int[] IMSSOFFLIN18_A34DFDomStaValOptOrd ;
   protected String[] IMSSOFFLIN18_A33DFDomStaValOptCod ;
   protected int[] IMSSOFFLIN18_A32DFDomId ;
   protected boolean[] IMSSOFFLIN18_n32DFDomId ;
   protected String[] IMSSOFFLIN19_A197DFFormInstSignedPDF ;
   protected boolean[] IMSSOFFLIN19_n197DFFormInstSignedPDF ;
   protected String[] IMSSOFFLIN19_A198DFFormInstSignedBy ;
   protected boolean[] IMSSOFFLIN19_n198DFFormInstSignedBy ;
   protected java.util.Date[] IMSSOFFLIN19_A155DFFormInstDT ;
   protected int[] IMSSOFFLIN19_A29DFFormInstFormVer ;
   protected int[] IMSSOFFLIN19_A28DFFormInstFormId ;
   protected long[] IMSSOFFLIN19_A9DFFormInstId ;
   protected boolean[] IMSSOFFLIN20_A305DFElemReq ;
   protected String[] IMSSOFFLIN20_A300DFElemLoadRule ;
   protected boolean[] IMSSOFFLIN20_n300DFElemLoadRule ;
   protected String[] IMSSOFFLIN20_A265DFElemMetadata ;
   protected boolean[] IMSSOFFLIN20_n265DFElemMetadata ;
   protected boolean[] IMSSOFFLIN20_A238DFElemIsColap ;
   protected String[] IMSSOFFLIN20_A306DFElemPrtPic ;
   protected boolean[] IMSSOFFLIN20_A280DFElemPrtShwNbr ;
   protected int[] IMSSOFFLIN20_A279DFElemPrtNumColSkip ;
   protected int[] IMSSOFFLIN20_A274DFElemPrtNumRowSkip ;
   protected boolean[] IMSSOFFLIN20_A272DFElemPrtAddRows ;
   protected String[] IMSSOFFLIN20_A269DFElemPrtName ;
   protected boolean[] IMSSOFFLIN20_A260DFElemIsVisPrt ;
   protected boolean[] IMSSOFFLIN20_A237DFElemIsVis ;
   protected String[] IMSSOFFLIN20_A257DFElemLblWth ;
   protected boolean[] IMSSOFFLIN20_n257DFElemLblWth ;
   protected String[] IMSSOFFLIN20_A243DFElemCmpWth ;
   protected boolean[] IMSSOFFLIN20_n243DFElemCmpWth ;
   protected String[] IMSSOFFLIN20_A242DFElemIsFlt ;
   protected boolean[] IMSSOFFLIN20_n242DFElemIsFlt ;
   protected String[] IMSSOFFLIN20_A256DFElemFileType ;
   protected boolean[] IMSSOFFLIN20_n256DFElemFileType ;
   protected String[] IMSSOFFLIN20_A254DFElemRegexVal ;
   protected boolean[] IMSSOFFLIN20_n254DFElemRegexVal ;
   protected boolean[] IMSSOFFLIN20_A253DFElemAllowDlt ;
   protected boolean[] IMSSOFFLIN20_n253DFElemAllowDlt ;
   protected boolean[] IMSSOFFLIN20_A252DFElemAllowUpd ;
   protected boolean[] IMSSOFFLIN20_n252DFElemAllowUpd ;
   protected boolean[] IMSSOFFLIN20_A251DFElemAllowIns ;
   protected boolean[] IMSSOFFLIN20_n251DFElemAllowIns ;
   protected boolean[] IMSSOFFLIN20_A250DFElemUseBtns ;
   protected boolean[] IMSSOFFLIN20_n250DFElemUseBtns ;
   protected boolean[] IMSSOFFLIN20_A249DFElemIsOrd ;
   protected boolean[] IMSSOFFLIN20_n249DFElemIsOrd ;
   protected int[] IMSSOFFLIN20_A248DFElemMaxSuggRes ;
   protected boolean[] IMSSOFFLIN20_n248DFElemMaxSuggRes ;
   protected boolean[] IMSSOFFLIN20_A247DFElemForceSuggSel ;
   protected boolean[] IMSSOFFLIN20_n247DFElemForceSuggSel ;
   protected int[] IMSSOFFLIN20_A246DFElemMinCntCharSugg ;
   protected boolean[] IMSSOFFLIN20_n246DFElemMinCntCharSugg ;
   protected String[] IMSSOFFLIN20_A258DFElemDscPrgName ;
   protected String[] IMSSOFFLIN20_A245DFElemLoadPrgName ;
   protected boolean[] IMSSOFFLIN20_n245DFElemLoadPrgName ;
   protected String[] IMSSOFFLIN20_A267DFElemBtnPos ;
   protected boolean[] IMSSOFFLIN20_n267DFElemBtnPos ;
   protected String[] IMSSOFFLIN20_A268DFElemShwNbrLbl ;
   protected boolean[] IMSSOFFLIN20_n268DFElemShwNbrLbl ;
   protected boolean[] IMSSOFFLIN20_A266DFElemShwNbr ;
   protected boolean[] IMSSOFFLIN20_n266DFElemShwNbr ;
   protected boolean[] IMSSOFFLIN20_A261DFElemDateSel ;
   protected boolean[] IMSSOFFLIN20_n261DFElemDateSel ;
   protected boolean[] IMSSOFFLIN20_A244DFElemHasPmpt ;
   protected boolean[] IMSSOFFLIN20_n244DFElemHasPmpt ;
   protected String[] IMSSOFFLIN20_A180DFElemDftVal ;
   protected boolean[] IMSSOFFLIN20_n180DFElemDftVal ;
   protected int[] IMSSOFFLIN20_A241DFElemCntCols ;
   protected boolean[] IMSSOFFLIN20_n241DFElemCntCols ;
   protected int[] IMSSOFFLIN20_A240DFElemCntRows ;
   protected boolean[] IMSSOFFLIN20_n240DFElemCntRows ;
   protected int[] IMSSOFFLIN20_A239DFElemCntDec ;
   protected boolean[] IMSSOFFLIN20_n239DFElemCntDec ;
   protected int[] IMSSOFFLIN20_A255DFElemWth ;
   protected boolean[] IMSSOFFLIN20_n255DFElemWth ;
   protected int[] IMSSOFFLIN20_A236DFElemLen ;
   protected boolean[] IMSSOFFLIN20_n236DFElemLen ;
   protected String[] IMSSOFFLIN20_A196DFElemDsp ;
   protected boolean[] IMSSOFFLIN20_n196DFElemDsp ;
   protected String[] IMSSOFFLIN20_A178DFElemType ;
   protected int[] IMSSOFFLIN20_A32DFDomId ;
   protected boolean[] IMSSOFFLIN20_n32DFDomId ;
   protected String[] IMSSOFFLIN20_A192DFElemClsName ;
   protected boolean[] IMSSOFFLIN20_n192DFElemClsName ;
   protected String[] IMSSOFFLIN20_A235DFElemDsc ;
   protected boolean[] IMSSOFFLIN20_n235DFElemDsc ;
   protected String[] IMSSOFFLIN20_A149DFElemName ;
   protected java.util.UUID[] IMSSOFFLIN20_A35DFElemGuid ;
   protected int[] IMSSOFFLIN20_A19DFElemVer ;
   protected int[] IMSSOFFLIN20_A18DFElemId ;
   protected String[] IMSSOFFLIN21_A71cveEspecialidad ;
   protected int[] IMSSOFFLIN21_A12DFFormVer ;
   protected int[] IMSSOFFLIN21_A11DFFormId ;
   protected java.util.Date[] IMSSOFFLIN22_A348PXDXFechaAsignacion ;
   protected short[] IMSSOFFLIN22_A347OcaSer ;
   protected short[] IMSSOFFLIN22_A346TpoDX ;
   protected int[] IMSSOFFLIN22_A345DX ;
   protected String[] IMSSOFFLIN22_A353IDEEPaciente ;
   protected boolean[] IMSSOFFLIN23_A310DFDomPrtDsc ;
   protected boolean[] IMSSOFFLIN23_n310DFDomPrtDsc ;
   protected String[] IMSSOFFLIN23_A223DFDomLblWth ;
   protected boolean[] IMSSOFFLIN23_n223DFDomLblWth ;
   protected String[] IMSSOFFLIN23_A219DFDomCmpWth ;
   protected boolean[] IMSSOFFLIN23_n219DFDomCmpWth ;
   protected String[] IMSSOFFLIN23_A218DFDomIsFlt ;
   protected boolean[] IMSSOFFLIN23_n218DFDomIsFlt ;
   protected String[] IMSSOFFLIN23_A221DFDomFileType ;
   protected boolean[] IMSSOFFLIN23_n221DFDomFileType ;
   protected String[] IMSSOFFLIN23_A217DFDomRegexVal ;
   protected boolean[] IMSSOFFLIN23_A213DFDomAllowDlt ;
   protected boolean[] IMSSOFFLIN23_n213DFDomAllowDlt ;
   protected boolean[] IMSSOFFLIN23_A212DFDomAllowUpd ;
   protected boolean[] IMSSOFFLIN23_n212DFDomAllowUpd ;
   protected boolean[] IMSSOFFLIN23_A211DFDomAllowIns ;
   protected boolean[] IMSSOFFLIN23_n211DFDomAllowIns ;
   protected boolean[] IMSSOFFLIN23_A210DFDomUseBtns ;
   protected boolean[] IMSSOFFLIN23_n210DFDomUseBtns ;
   protected boolean[] IMSSOFFLIN23_A209DFDomIsOrd ;
   protected boolean[] IMSSOFFLIN23_n209DFDomIsOrd ;
   protected int[] IMSSOFFLIN23_A207DFDomMaxSuggRes ;
   protected boolean[] IMSSOFFLIN23_n207DFDomMaxSuggRes ;
   protected boolean[] IMSSOFFLIN23_A206DFDomForceSuggSel ;
   protected boolean[] IMSSOFFLIN23_n206DFDomForceSuggSel ;
   protected int[] IMSSOFFLIN23_A205DFDomMinCntCharSugg ;
   protected boolean[] IMSSOFFLIN23_n205DFDomMinCntCharSugg ;
   protected String[] IMSSOFFLIN23_A208DFDomDftVal ;
   protected boolean[] IMSSOFFLIN23_n208DFDomDftVal ;
   protected int[] IMSSOFFLIN23_A216DFDomCntCols ;
   protected int[] IMSSOFFLIN23_A215DFDomCntRows ;
   protected int[] IMSSOFFLIN23_A214DFDomCntDec ;
   protected int[] IMSSOFFLIN23_A220DFDomWth ;
   protected int[] IMSSOFFLIN23_A204DFDomLen ;
   protected String[] IMSSOFFLIN23_A195DFDomDsp ;
   protected boolean[] IMSSOFFLIN23_n195DFDomDsp ;
   protected String[] IMSSOFFLIN23_A194DFDomType ;
   protected java.util.UUID[] IMSSOFFLIN23_A224DFDomGUID ;
   protected String[] IMSSOFFLIN23_A203DFDomDsc ;
   protected int[] IMSSOFFLIN23_A32DFDomId ;
   protected boolean[] IMSSOFFLIN23_n32DFDomId ;
   protected String[] IMSSOFFLIN24_A14DFFormRstVal ;
   protected int[] IMSSOFFLIN24_A13DFFormRstId ;
   protected int[] IMSSOFFLIN24_A12DFFormVer ;
   protected int[] IMSSOFFLIN24_A11DFFormId ;
   protected boolean[] IMSSOFFLIN25_A164DFUserRstPwdIni ;
   protected String[] IMSSOFFLIN25_A24DFUserRstVal ;
   protected int[] IMSSOFFLIN25_A23DFUserRstId ;
   protected String[] IMSSOFFLIN25_A22DFUserExtId ;
   protected int[] IMSSOFFLIN26_A39DFSubElemFormPos ;
   protected boolean[] IMSSOFFLIN26_n39DFSubElemFormPos ;
   protected int[] IMSSOFFLIN26_A38DFSubElemFormElemVer ;
   protected int[] IMSSOFFLIN26_A37DFSubElemFormElemId ;
   protected int[] IMSSOFFLIN26_A19DFElemVer ;
   protected int[] IMSSOFFLIN26_A18DFElemId ;
   protected int[] IMSSOFFLIN26_A12DFFormVer ;
   protected int[] IMSSOFFLIN26_A11DFFormId ;
   protected int[] IMSSOFFLIN27_A42DFFilElemFormElemVer ;
   protected int[] IMSSOFFLIN27_A41DFFilElemFormElemId ;
   protected short[] IMSSOFFLIN27_A43DFFilElemFormPos ;
   protected int[] IMSSOFFLIN27_A40DFFilElemFormId ;
   protected int[] IMSSOFFLIN27_A19DFElemVer ;
   protected int[] IMSSOFFLIN27_A18DFElemId ;
   protected int[] IMSSOFFLIN27_A12DFFormVer ;
   protected int[] IMSSOFFLIN27_A11DFFormId ;
   protected short[] IMSSOFFLIN28_A7HospitalId ;
   protected boolean[] IMSSOFFLIN28_n7HospitalId ;
   protected String[] IMSSOFFLIN28_A104ServicioDescripcion ;
   protected short[] IMSSOFFLIN28_A6ServicioId ;
   protected int[] IMSSOFFLIN29_A12DFFormVer ;
   protected int[] IMSSOFFLIN29_A11DFFormId ;
   protected java.util.Date[] IMSSOFFLIN29_A321fecBajaEspecialidad ;
   protected boolean[] IMSSOFFLIN29_n321fecBajaEspecialidad ;
   protected String[] IMSSOFFLIN29_A320desEspecialidad ;
   protected String[] IMSSOFFLIN29_A71cveEspecialidad ;
   protected int[] IMSSOFFLIN30_A28DFFormInstFormId ;
   protected String[] IMSSOFFLIN30_A139DFUplFileExt ;
   protected String[] IMSSOFFLIN30_A140DFUplFileName ;
   protected String[] IMSSOFFLIN30_A138DFUplFile ;
   protected String[] IMSSOFFLIN30_A10DFUplKey ;
   protected long[] IMSSOFFLIN30_A9DFFormInstId ;
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
                                               String A133PacienteNSSAgregado ,
                                               GxObjectCollection AV3ColPacienteNSSAgregado ,
                                               String A8Matricula ,
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

   protected Object[] conditional_IMSSOFFLIN6( ModelContext context ,
                                               int remoteHandle ,
                                               com.genexus.internet.HttpContext httpContext ,
                                               String A133PacienteNSSAgregado ,
                                               GxObjectCollection AV3ColPacienteNSSAgregado )
   {
      String sWhereString = "" ;
      String scmdbuf ;
      Object[] GXv_Object12 ;
      GXv_Object12 = new Object [2] ;
      scmdbuf = "SELECT T2.PacienteNSSAgregado, T1.MMatricula, T1.MApMat, T1.MApPat, T1.MNombre, T1.MBMatricula," ;
      scmdbuf = scmdbuf + " T1.MBApMat, T1.MBApPat, T1.MBNombre, T1.JSMatricula, T1.JSApMat, T1.JSApPat, T1.JSNombre," ;
      scmdbuf = scmdbuf + " T1.DiagnosticoCirugiaFecha, T1.DiagnosticoCirugia, T1.Cama, T1.ServicioId, T1.DiagnosticoComplemento," ;
      scmdbuf = scmdbuf + " T1.DiagnosticoResumen, T1.DiagnosticoFechaAlta, T1.DiagnosticoFechaIngreso, T1.CIE10Id," ;
      scmdbuf = scmdbuf + " T1.PacienteAgregado, T1.PacienteNSS FROM (ExpedienteDiagnostico T1 INNER JOIN Paciente" ;
      scmdbuf = scmdbuf + " T2 ON T2.PacienteNSS = T1.PacienteNSS AND T2.PacienteAgregado = T1.PacienteAgregado)" ;
      scmdbuf = scmdbuf + " WHERE (" + GXutil.toValueList("postgresql", AV3ColPacienteNSSAgregado, "T2.PacienteNSSAgregado IN (", ")") + ")" ;
      scmdbuf = scmdbuf + sWhereString ;
      scmdbuf = scmdbuf + " ORDER BY T1.PacienteNSS, T1.PacienteAgregado, T1.CIE10Id" ;
      GXv_Object12[0] = scmdbuf ;
      return GXv_Object12 ;
   }

   protected Object[] conditional_IMSSOFFLIN8( ModelContext context ,
                                               int remoteHandle ,
                                               com.genexus.internet.HttpContext httpContext ,
                                               String A133PacienteNSSAgregado ,
                                               GxObjectCollection AV3ColPacienteNSSAgregado )
   {
      String sWhereString = "" ;
      String scmdbuf ;
      Object[] GXv_Object15 ;
      GXv_Object15 = new Object [2] ;
      scmdbuf = "SELECT T2.PacienteNSSAgregado, T1.DXAuxImagenImg_GXI, T1.DXAuxImagenUserAlta, T1.DXAuxImagenFechaAlta," ;
      scmdbuf = scmdbuf + " T1.DXAuxImagenImg, T1.DXAuxImagenExtension, T1.DXAuxImagenNombre, T1.DXAuxImagenId," ;
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
                                               String A133PacienteNSSAgregado ,
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
                                                String A133PacienteNSSAgregado ,
                                                GxObjectCollection AV3ColPacienteNSSAgregado )
   {
      String sWhereString = "" ;
      String scmdbuf ;
      Object[] GXv_Object21 ;
      GXv_Object21 = new Object [2] ;
      scmdbuf = "SELECT ClavePresupuestal, IDEE, CURP, DhUMF, DhDeleg, Consultorio, ConDerechoSm," ;
      scmdbuf = scmdbuf + " ConDerechoInc, PacienteServicioId, PacienteCie10Id, PacienteNSSAgregado, PacienteCama," ;
      scmdbuf = scmdbuf + " PacienteDiagnosticoPhone, PacienteDiagnosticoResumido, PacienteDiagnostico, PAcienteFechaIngreso," ;
      scmdbuf = scmdbuf + " PacienteNombreCompleto, PacienteReferencia, PacienteFamiliar, PacienteTelefono," ;
      scmdbuf = scmdbuf + " PacienteGenero, PacienteEdad, PacienteFechaNacimiento, PacienteApMat, PacienteApPat," ;
      scmdbuf = scmdbuf + " PacienteNombre, PacienteAgregado, PacienteNSS FROM Paciente" ;
      scmdbuf = scmdbuf + " WHERE (" + GXutil.toValueList("postgresql", AV3ColPacienteNSSAgregado, "PacienteNSSAgregado IN (", ")") + ")" ;
      scmdbuf = scmdbuf + sWhereString ;
      scmdbuf = scmdbuf + " ORDER BY PacienteNSS, PacienteAgregado" ;
      GXv_Object21[0] = scmdbuf ;
      return GXv_Object21 ;
   }

   protected Object[] conditional_IMSSOFFLIN12( ModelContext context ,
                                                int remoteHandle ,
                                                com.genexus.internet.HttpContext httpContext ,
                                                long A9DFFormInstId ,
                                                GxObjectCollection AV2ColDFFormInstId )
   {
      String sWhereString = "" ;
      String scmdbuf ;
      Object[] GXv_Object24 ;
      GXv_Object24 = new Object [2] ;
      scmdbuf = "SELECT FormatoPacienteMedicoMatricula, FormatoPacienteMedicoNombre, DFFormInstId," ;
      scmdbuf = scmdbuf + " FormatoPacienteAgregado, FormatoPacienteNSS FROM FormatoPaciente" ;
      scmdbuf = scmdbuf + " WHERE (" + GXutil.toValueList("postgresql", AV2ColDFFormInstId, "DFFormInstId IN (", ")") + ")" ;
      scmdbuf = scmdbuf + sWhereString ;
      scmdbuf = scmdbuf + " ORDER BY FormatoPacienteNSS, FormatoPacienteAgregado, DFFormInstId" ;
      GXv_Object24[0] = scmdbuf ;
      return GXv_Object24 ;
   }

   protected Object[] conditional_IMSSOFFLIN14( ModelContext context ,
                                                int remoteHandle ,
                                                com.genexus.internet.HttpContext httpContext ,
                                                long A9DFFormInstId ,
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

   protected Object[] conditional_IMSSOFFLIN15( ModelContext context ,
                                                int remoteHandle ,
                                                com.genexus.internet.HttpContext httpContext ,
                                                long A9DFFormInstId ,
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
                                                long A9DFFormInstId ,
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

   protected Object[] conditional_IMSSOFFLIN30( ModelContext context ,
                                                int remoteHandle ,
                                                com.genexus.internet.HttpContext httpContext ,
                                                long A9DFFormInstId ,
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
            case 4 :
                  return conditional_IMSSOFFLIN6(context, remoteHandle, httpContext, (String)dynConstraints[0] , (GxObjectCollection)dynConstraints[1] );
            case 6 :
                  return conditional_IMSSOFFLIN8(context, remoteHandle, httpContext, (String)dynConstraints[0] , (GxObjectCollection)dynConstraints[1] );
            case 7 :
                  return conditional_IMSSOFFLIN9(context, remoteHandle, httpContext, (String)dynConstraints[0] , (GxObjectCollection)dynConstraints[1] );
            case 8 :
                  return conditional_IMSSOFFLIN10(context, remoteHandle, httpContext, (String)dynConstraints[0] , (GxObjectCollection)dynConstraints[1] );
            case 10 :
                  return conditional_IMSSOFFLIN12(context, remoteHandle, httpContext, ((Number) dynConstraints[0]).longValue() , (GxObjectCollection)dynConstraints[1] );
            case 12 :
                  return conditional_IMSSOFFLIN14(context, remoteHandle, httpContext, ((Number) dynConstraints[0]).longValue() , (GxObjectCollection)dynConstraints[1] );
            case 13 :
                  return conditional_IMSSOFFLIN15(context, remoteHandle, httpContext, ((Number) dynConstraints[0]).longValue() , (GxObjectCollection)dynConstraints[1] );
            case 17 :
                  return conditional_IMSSOFFLIN19(context, remoteHandle, httpContext, ((Number) dynConstraints[0]).longValue() , (GxObjectCollection)dynConstraints[1] );
            case 28 :
                  return conditional_IMSSOFFLIN30(context, remoteHandle, httpContext, ((Number) dynConstraints[0]).longValue() , (GxObjectCollection)dynConstraints[1] );
      }
      return super.getDynamicStatement(cursor, context, remoteHandle, httpContext, dynConstraints);
   }

   public Cursor[] getCursors( )
   {
      return new Cursor[] {
          new ForEachCursor("IMSSOFFLIN2", "SELECT FecBajaMed, MedDebMosTerm, MedDebValDat, MedUltAct, MedCedProf, MedApMat, MedApPat, MedNom, UserMed, MedMatricula FROM Medico WHERE UserMed = ( ?) ORDER BY MedMatricula ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN3", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN4", "SELECT DFParmIsMetaData, DFParmVal, DFParmName, DFParmId FROM DFParm ORDER BY DFParmId ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN5", "SELECT CIE10Descripcion, CIECodigo, CIE10Id FROM CIE10 ORDER BY CIE10Id ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN6", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN7", "SELECT nada, TextoDescripcion, TextoTitulo, TextoId FROM Texto ORDER BY TextoId ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN8", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN9", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN10", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN11", "SELECT ExtensionNombre, ExtensionTipo, ExtensionId FROM Extension ORDER BY ExtensionId ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN12", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN13", "SELECT DFElemFormReq, DFElemFormLoadRule, DFElemFormMetadata, DFElemFormShwNbr, DFElemFormDateSel, DFElemFormHasPmpt, DFElemFormIsFlt, DFElemFormCmpWth, DFElemFormLblWth, DFElemFormPrtPic, DFElemFormPrtShwNbr, DFElemFormPrtNumColSkip, DFElemFormPrtNumRowSkip, DFElemFormPrtAddRows, DFElemFormPrtName, DFElemFormIsVisPrt, DFElemFormIsVis, DFElemFormIsColap, DFElemFormAllowIns, DFElemFormAllowUpd, DFElemFormAllowDlt, DFElemFormInhType, DFElemFormPos, DFElemFormName, DFElemVer, DFElemId, DFFormVer, DFFormId FROM DFElemForm ORDER BY DFFormId, DFFormVer, DFElemId, DFElemVer ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN14", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN15", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN16", "SELECT DFTempOutFm, DFTempAddParmPrgName, DFTempBlob, DFTempFm, DFTempDsc, DFTempName, DFFormVer, DFFormId FROM DFTemp ORDER BY DFFormId, DFFormVer, DFTempName ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN17", "SELECT DFFormIsSD, DFFormRunDLT, DFFormHelpURL, DFFormPrefix, DFFormPmtHgh, DFFormPmtWth, DFFormAct, DFFormDsc, DFFormName, DFFormGuid, DFFormVer, DFFormId FROM DFForm ORDER BY DFFormId, DFFormVer ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN18", "SELECT DFDomStaValOptDsc, DFDomStaValOptOrd, DFDomStaValOptCod, DFDomId FROM DFDomStaVals ORDER BY DFDomId, DFDomStaValOptCod ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN19", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN20", "SELECT DFElemReq, DFElemLoadRule, DFElemMetadata, DFElemIsColap, DFElemPrtPic, DFElemPrtShwNbr, DFElemPrtNumColSkip, DFElemPrtNumRowSkip, DFElemPrtAddRows, DFElemPrtName, DFElemIsVisPrt, DFElemIsVis, DFElemLblWth, DFElemCmpWth, DFElemIsFlt, DFElemFileType, DFElemRegexVal, DFElemAllowDlt, DFElemAllowUpd, DFElemAllowIns, DFElemUseBtns, DFElemIsOrd, DFElemMaxSuggRes, DFElemForceSuggSel, DFElemMinCntCharSugg, DFElemDscPrgName, DFElemLoadPrgName, DFElemBtnPos, DFElemShwNbrLbl, DFElemShwNbr, DFElemDateSel, DFElemHasPmpt, DFElemDftVal, DFElemCntCols, DFElemCntRows, DFElemCntDec, DFElemWth, DFElemLen, DFElemDsp, DFElemType, DFDomId, DFElemClsName, DFElemDsc, DFElemName, DFElemGuid, DFElemVer, DFElemId FROM DFElem ORDER BY DFElemId, DFElemVer ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN21", "SELECT cveEspecialidad, DFFormVer, DFFormId FROM EspecialidadFormato ORDER BY DFFormId, DFFormVer, cveEspecialidad ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN22", "SELECT PXDXFechaAsignacion, OcaSer, TpoDX, DX, IDEEPaciente FROM PacienteDiagnostico ORDER BY IDEEPaciente, DX ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN23", "SELECT DFDomPrtDsc, DFDomLblWth, DFDomCmpWth, DFDomIsFlt, DFDomFileType, DFDomRegexVal, DFDomAllowDlt, DFDomAllowUpd, DFDomAllowIns, DFDomUseBtns, DFDomIsOrd, DFDomMaxSuggRes, DFDomForceSuggSel, DFDomMinCntCharSugg, DFDomDftVal, DFDomCntCols, DFDomCntRows, DFDomCntDec, DFDomWth, DFDomLen, DFDomDsp, DFDomType, DFDomGUID, DFDomDsc, DFDomId FROM DFDom ORDER BY DFDomId ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN24", "SELECT DFFormRstVal, DFFormRstId, DFFormVer, DFFormId FROM DFFormRst ORDER BY DFFormId, DFFormVer, DFFormRstId, DFFormRstVal ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN25", "SELECT DFUserRstPwdIni, DFUserRstVal, DFUserRstId, DFUserExtId FROM DFUserRst ORDER BY DFUserExtId, DFUserRstId, DFUserRstVal ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN26", "SELECT DFSubElemFormPos, DFSubElemFormElemVer, DFSubElemFormElemId, DFElemVer, DFElemId, DFFormVer, DFFormId FROM DFSubElemForm ORDER BY DFFormId, DFFormVer, DFElemId, DFElemVer, DFSubElemFormElemId, DFSubElemFormElemVer ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN27", "SELECT DFFilElemFormElemVer, DFFilElemFormElemId, DFFilElemFormPos, DFFilElemFormId, DFElemVer, DFElemId, DFFormVer, DFFormId FROM DFFilElemForm ORDER BY DFFormId, DFFormVer, DFElemId, DFElemVer, DFFilElemFormId ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN28", "SELECT HospitalId, ServicioDescripcion, ServicioId FROM Servicio ORDER BY ServicioId ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN29", "SELECT DISTINCT NULL AS DFFormVer, NULL AS DFFormId, fecBajaEspecialidad, desEspecialidad, cveEspecialidad FROM ( SELECT T1.DFFormVer, T1.DFFormId, T2.fecBajaEspecialidad, T2.desEspecialidad, T1.cveEspecialidad FROM (EspecialidadFormato T1 INNER JOIN SIC_ESPECIALIDAD T2 ON T2.cveEspecialidad = T1.cveEspecialidad) ORDER BY T1.cveEspecialidad) DistinctT ORDER BY cveEspecialidad ",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
         ,new ForEachCursor("IMSSOFFLIN30", "scmdbuf",false, GX_NOMASK + GX_MASKLOOPLOCK, false, this,100,0,false )
      };
   }

   public void getResults( int cursor ,
                           IFieldGetter rslt ,
                           Object[] buf ) throws SQLException
   {
      switch ( cursor )
      {
            case 0 :
               ((java.util.Date[]) buf[0])[0] = rslt.getGXDate(1) ;
               ((boolean[]) buf[1])[0] = rslt.wasNull();
               ((boolean[]) buf[2])[0] = rslt.getBoolean(2) ;
               ((boolean[]) buf[3])[0] = rslt.wasNull();
               ((boolean[]) buf[4])[0] = rslt.getBoolean(3) ;
               ((java.util.Date[]) buf[5])[0] = rslt.getGXDateTime(4) ;
               ((String[]) buf[6])[0] = rslt.getString(5, 10) ;
               ((String[]) buf[7])[0] = rslt.getString(6, 40) ;
               ((String[]) buf[8])[0] = rslt.getString(7, 40) ;
               ((String[]) buf[9])[0] = rslt.getString(8, 40) ;
               ((String[]) buf[10])[0] = rslt.getString(9, 30) ;
               ((long[]) buf[11])[0] = rslt.getLong(10) ;
               return;
            case 1 :
               ((String[]) buf[0])[0] = rslt.getVarchar(1) ;
               ((String[]) buf[1])[0] = rslt.getString(2, 20) ;
               ((String[]) buf[2])[0] = rslt.getString(3, 8) ;
               ((String[]) buf[3])[0] = rslt.getString(4, 11) ;
               return;
            case 2 :
               ((boolean[]) buf[0])[0] = rslt.getBoolean(1) ;
               ((String[]) buf[1])[0] = rslt.getString(2, 200) ;
               ((String[]) buf[2])[0] = rslt.getString(3, 100) ;
               ((int[]) buf[3])[0] = rslt.getInt(4) ;
               return;
            case 3 :
               ((String[]) buf[0])[0] = rslt.getVarchar(1) ;
               ((String[]) buf[1])[0] = rslt.getVarchar(2) ;
               ((int[]) buf[2])[0] = rslt.getInt(3) ;
               return;
            case 4 :
               ((String[]) buf[0])[0] = rslt.getVarchar(1) ;
               ((short[]) buf[1])[0] = rslt.getShort(2) ;
               ((boolean[]) buf[2])[0] = rslt.wasNull();
               ((short[]) buf[3])[0] = rslt.getShort(3) ;
               ((boolean[]) buf[4])[0] = rslt.wasNull();
               ((short[]) buf[5])[0] = rslt.getShort(4) ;
               ((boolean[]) buf[6])[0] = rslt.wasNull();
               ((short[]) buf[7])[0] = rslt.getShort(5) ;
               ((boolean[]) buf[8])[0] = rslt.wasNull();
               ((short[]) buf[9])[0] = rslt.getShort(6) ;
               ((boolean[]) buf[10])[0] = rslt.wasNull();
               ((String[]) buf[11])[0] = rslt.getString(7, 40) ;
               ((boolean[]) buf[12])[0] = rslt.wasNull();
               ((String[]) buf[13])[0] = rslt.getString(8, 40) ;
               ((boolean[]) buf[14])[0] = rslt.wasNull();
               ((String[]) buf[15])[0] = rslt.getString(9, 40) ;
               ((boolean[]) buf[16])[0] = rslt.wasNull();
               ((short[]) buf[17])[0] = rslt.getShort(10) ;
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
            case 5 :
               ((short[]) buf[0])[0] = rslt.getShort(1) ;
               ((String[]) buf[1])[0] = rslt.getLongVarchar(2) ;
               ((String[]) buf[2])[0] = rslt.getVarchar(3) ;
               ((short[]) buf[3])[0] = rslt.getShort(4) ;
               return;
            case 6 :
               ((String[]) buf[0])[0] = rslt.getVarchar(1) ;
               ((String[]) buf[1])[0] = rslt.getMultimediaUri(2) ;
               ((String[]) buf[2])[0] = rslt.getString(3, 30) ;
               ((java.util.Date[]) buf[3])[0] = rslt.getGXDateTime(4) ;
               ((String[]) buf[4])[0] = rslt.getMultimediaFile(5, rslt.getVarchar(2)) ;
               ((String[]) buf[5])[0] = rslt.getString(6, 10) ;
               ((String[]) buf[6])[0] = rslt.getString(7, 40) ;
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
               ((String[]) buf[0])[0] = rslt.getString(1, 18) ;
               ((String[]) buf[1])[0] = rslt.getString(2, 18) ;
               ((boolean[]) buf[2])[0] = rslt.wasNull();
               ((String[]) buf[3])[0] = rslt.getString(3, 18) ;
               ((boolean[]) buf[4])[0] = rslt.wasNull();
               ((String[]) buf[5])[0] = rslt.getString(4, 3) ;
               ((boolean[]) buf[6])[0] = rslt.wasNull();
               ((String[]) buf[7])[0] = rslt.getString(5, 2) ;
               ((boolean[]) buf[8])[0] = rslt.wasNull();
               ((String[]) buf[9])[0] = rslt.getString(6, 14) ;
               ((boolean[]) buf[10])[0] = rslt.wasNull();
               ((String[]) buf[11])[0] = rslt.getString(7, 2) ;
               ((boolean[]) buf[12])[0] = rslt.wasNull();
               ((String[]) buf[13])[0] = rslt.getString(8, 2) ;
               ((boolean[]) buf[14])[0] = rslt.wasNull();
               ((short[]) buf[15])[0] = rslt.getShort(9) ;
               ((int[]) buf[16])[0] = rslt.getInt(10) ;
               ((String[]) buf[17])[0] = rslt.getVarchar(11) ;
               ((String[]) buf[18])[0] = rslt.getString(12, 6) ;
               ((String[]) buf[19])[0] = rslt.getVarchar(13) ;
               ((String[]) buf[20])[0] = rslt.getVarchar(14) ;
               ((String[]) buf[21])[0] = rslt.getVarchar(15) ;
               ((java.util.Date[]) buf[22])[0] = rslt.getGXDate(16) ;
               ((String[]) buf[23])[0] = rslt.getString(17, 150) ;
               ((String[]) buf[24])[0] = rslt.getString(18, 50) ;
               ((boolean[]) buf[25])[0] = rslt.wasNull();
               ((String[]) buf[26])[0] = rslt.getVarchar(19) ;
               ((boolean[]) buf[27])[0] = rslt.wasNull();
               ((String[]) buf[28])[0] = rslt.getString(20, 20) ;
               ((boolean[]) buf[29])[0] = rslt.wasNull();
               ((String[]) buf[30])[0] = rslt.getString(21, 1) ;
               ((boolean[]) buf[31])[0] = rslt.wasNull();
               ((short[]) buf[32])[0] = rslt.getShort(22) ;
               ((java.util.Date[]) buf[33])[0] = rslt.getGXDate(23) ;
               ((String[]) buf[34])[0] = rslt.getString(24, 40) ;
               ((boolean[]) buf[35])[0] = rslt.wasNull();
               ((String[]) buf[36])[0] = rslt.getString(25, 40) ;
               ((String[]) buf[37])[0] = rslt.getString(26, 40) ;
               ((String[]) buf[38])[0] = rslt.getString(27, 8) ;
               ((String[]) buf[39])[0] = rslt.getString(28, 11) ;
               return;
            case 9 :
               ((String[]) buf[0])[0] = rslt.getString(1, 40) ;
               ((short[]) buf[1])[0] = rslt.getShort(2) ;
               ((short[]) buf[2])[0] = rslt.getShort(3) ;
               return;
            case 10 :
               ((long[]) buf[0])[0] = rslt.getLong(1) ;
               ((String[]) buf[1])[0] = rslt.getVarchar(2) ;
               ((long[]) buf[2])[0] = rslt.getLong(3) ;
               ((String[]) buf[3])[0] = rslt.getString(4, 8) ;
               ((String[]) buf[4])[0] = rslt.getString(5, 11) ;
               return;
            case 11 :
               ((boolean[]) buf[0])[0] = rslt.getBoolean(1) ;
               ((String[]) buf[1])[0] = rslt.getVarchar(2) ;
               ((boolean[]) buf[2])[0] = rslt.wasNull();
               ((String[]) buf[3])[0] = rslt.getVarchar(3) ;
               ((boolean[]) buf[4])[0] = rslt.wasNull();
               ((boolean[]) buf[5])[0] = rslt.getBoolean(4) ;
               ((boolean[]) buf[6])[0] = rslt.wasNull();
               ((boolean[]) buf[7])[0] = rslt.getBoolean(5) ;
               ((boolean[]) buf[8])[0] = rslt.wasNull();
               ((boolean[]) buf[9])[0] = rslt.getBoolean(6) ;
               ((boolean[]) buf[10])[0] = rslt.wasNull();
               ((String[]) buf[11])[0] = rslt.getString(7, 20) ;
               ((boolean[]) buf[12])[0] = rslt.wasNull();
               ((String[]) buf[13])[0] = rslt.getString(8, 20) ;
               ((boolean[]) buf[14])[0] = rslt.wasNull();
               ((String[]) buf[15])[0] = rslt.getString(9, 20) ;
               ((boolean[]) buf[16])[0] = rslt.wasNull();
               ((String[]) buf[17])[0] = rslt.getVarchar(10) ;
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
            case 12 :
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
            case 13 :
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
            case 14 :
               ((String[]) buf[0])[0] = rslt.getString(1, 1) ;
               ((String[]) buf[1])[0] = rslt.getVarchar(2) ;
               ((String[]) buf[2])[0] = rslt.getBLOBFile(3, "tmp", "") ;
               ((String[]) buf[3])[0] = rslt.getString(4, 1) ;
               ((String[]) buf[4])[0] = rslt.getVarchar(5) ;
               ((String[]) buf[5])[0] = rslt.getString(6, 100) ;
               ((int[]) buf[6])[0] = rslt.getInt(7) ;
               ((int[]) buf[7])[0] = rslt.getInt(8) ;
               return;
            case 15 :
               ((boolean[]) buf[0])[0] = rslt.getBoolean(1) ;
               ((boolean[]) buf[1])[0] = rslt.getBoolean(2) ;
               ((String[]) buf[2])[0] = rslt.getVarchar(3) ;
               ((String[]) buf[3])[0] = rslt.getVarchar(4) ;
               ((int[]) buf[4])[0] = rslt.getInt(5) ;
               ((boolean[]) buf[5])[0] = rslt.wasNull();
               ((int[]) buf[6])[0] = rslt.getInt(6) ;
               ((boolean[]) buf[7])[0] = rslt.wasNull();
               ((boolean[]) buf[8])[0] = rslt.getBoolean(7) ;
               ((String[]) buf[9])[0] = rslt.getVarchar(8) ;
               ((String[]) buf[10])[0] = rslt.getString(9, 100) ;
               ((java.util.UUID[]) buf[11])[0] = rslt.getGUID(10) ;
               ((int[]) buf[12])[0] = rslt.getInt(11) ;
               ((int[]) buf[13])[0] = rslt.getInt(12) ;
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
               ((boolean[]) buf[2])[0] = rslt.wasNull();
               ((String[]) buf[3])[0] = rslt.getVarchar(3) ;
               ((boolean[]) buf[4])[0] = rslt.wasNull();
               ((boolean[]) buf[5])[0] = rslt.getBoolean(4) ;
               ((String[]) buf[6])[0] = rslt.getVarchar(5) ;
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
               ((String[]) buf[0])[0] = rslt.getString(1, 4) ;
               ((int[]) buf[1])[0] = rslt.getInt(2) ;
               ((int[]) buf[2])[0] = rslt.getInt(3) ;
               return;
            case 20 :
               ((java.util.Date[]) buf[0])[0] = rslt.getGXDateTime(1) ;
               ((short[]) buf[1])[0] = rslt.getShort(2) ;
               ((short[]) buf[2])[0] = rslt.getShort(3) ;
               ((int[]) buf[3])[0] = rslt.getInt(4) ;
               ((String[]) buf[4])[0] = rslt.getString(5, 18) ;
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
               ((String[]) buf[0])[0] = rslt.getString(1, 200) ;
               ((int[]) buf[1])[0] = rslt.getInt(2) ;
               ((int[]) buf[2])[0] = rslt.getInt(3) ;
               ((int[]) buf[3])[0] = rslt.getInt(4) ;
               return;
            case 23 :
               ((boolean[]) buf[0])[0] = rslt.getBoolean(1) ;
               ((String[]) buf[1])[0] = rslt.getString(2, 200) ;
               ((int[]) buf[2])[0] = rslt.getInt(3) ;
               ((String[]) buf[3])[0] = rslt.getVarchar(4) ;
               return;
            case 24 :
               ((int[]) buf[0])[0] = rslt.getInt(1) ;
               ((boolean[]) buf[1])[0] = rslt.wasNull();
               ((int[]) buf[2])[0] = rslt.getInt(2) ;
               ((int[]) buf[3])[0] = rslt.getInt(3) ;
               ((int[]) buf[4])[0] = rslt.getInt(4) ;
               ((int[]) buf[5])[0] = rslt.getInt(5) ;
               ((int[]) buf[6])[0] = rslt.getInt(6) ;
               ((int[]) buf[7])[0] = rslt.getInt(7) ;
               return;
            case 25 :
               ((int[]) buf[0])[0] = rslt.getInt(1) ;
               ((int[]) buf[1])[0] = rslt.getInt(2) ;
               ((short[]) buf[2])[0] = rslt.getShort(3) ;
               ((int[]) buf[3])[0] = rslt.getInt(4) ;
               ((int[]) buf[4])[0] = rslt.getInt(5) ;
               ((int[]) buf[5])[0] = rslt.getInt(6) ;
               ((int[]) buf[6])[0] = rslt.getInt(7) ;
               ((int[]) buf[7])[0] = rslt.getInt(8) ;
               return;
            case 26 :
               ((short[]) buf[0])[0] = rslt.getShort(1) ;
               ((boolean[]) buf[1])[0] = rslt.wasNull();
               ((String[]) buf[2])[0] = rslt.getString(2, 30) ;
               ((short[]) buf[3])[0] = rslt.getShort(3) ;
               return;
            case 27 :
               ((int[]) buf[0])[0] = rslt.getInt(1) ;
               ((int[]) buf[1])[0] = rslt.getInt(2) ;
               ((java.util.Date[]) buf[2])[0] = rslt.getGXDate(3) ;
               ((boolean[]) buf[3])[0] = rslt.wasNull();
               ((String[]) buf[4])[0] = rslt.getVarchar(4) ;
               ((String[]) buf[5])[0] = rslt.getString(5, 4) ;
               return;
            case 28 :
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

