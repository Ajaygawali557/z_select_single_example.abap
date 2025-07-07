# z_select_single_example.abap
REPORT z_select_single_example.

TABLES: mara.

DATA: lv_matnr TYPE mara-matnr,
      lv_mtart TYPE mara-mtart.

PARAMETERS: p_matnr TYPE mara-matnr.

SELECT SINGLE matnr mtart
  INTO (lv_matnr, lv_mtart)
  FROM mara
  WHERE matnr = p_matnr.

IF sy-subrc = 0.
  WRITE: / 'Material:', lv_matnr, 'Type:', lv_mtart.
ELSE.
  WRITE: / 'Material not found'.
ENDIF.
