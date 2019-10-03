---
title: Stosowanie transformacji XSLT do elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09f2e4ee-1d08-4ba8-8936-83394fee319d
ms.openlocfilehash: 2641637d176b411108aeb2fa00ef4268584e9cb3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834271"
---
# <a name="applying-an-xslt-transform-to-a-dataset"></a>Stosowanie transformacji XSLT do elementu DataSet

@No__t Metoda **WriteXml** -1 umożliwia zapisanie zawartości **zestawu** danych jako danych XML. Typowym zadaniem jest następnie przekształcenie tego pliku XML do innego formatu przy użyciu transformacji XSL (XSLT). Jednak synchronizowanie **zestawu danych** z <xref:System.Xml.XmlDataDocument> umożliwia zastosowanie arkusza stylów XSLT do zawartości **zestawu danych** bez konieczności uprzedniego zapisania zawartości **zestawu danych** jako danych XML przy użyciu **WriteXml**.  
  
 Poniższy przykład wypełnia **zestaw danych** z tabelami i relacjami, synchronizuje **zestaw danych** z **XmlDataDocument**i zapisuje część **zestawu danych** jako plik HTML przy użyciu arkusza stylów XSLT. Poniżej znajduje się zawartość arkusza stylów XSLT:
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
<xsl:template match="CustomerOrders">  
  <HTML>  
  <STYLE>  
  BODY {font-family:verdana;font-size:9pt}  
  TD   {font-size:8pt}  
  </STYLE>  
    <BODY>  
    <TABLE BORDER="1">  
      <xsl:apply-templates select="Customers"/>  
    </TABLE>  
    </BODY>  
  </HTML>  
</xsl:template>  
  
<xsl:template match="Customers">  
    <TR><TD>  
      <xsl:value-of select="ContactName"/>, <xsl:value-of select="Phone"/><BR/>  
    </TD></TR>  
      <xsl:apply-templates select="Orders"/>  
</xsl:template>  
  
<xsl:template match="Orders">  
  <TABLE BORDER="1">  
    <TR><TD valign="top"><B>Order:</B></TD><TD valign="top"><xsl:value-of select="OrderID"/></TD></TR>  
    <TR><TD valign="top"><B>Date:</B></TD><TD valign="top"><xsl:value-of select="OrderDate"/></TD></TR>  
    <TR><TD valign="top"><B>Ship To:</B></TD>  
        <TD valign="top"><xsl:value-of select="ShipName"/><BR/>  
        <xsl:value-of select="ShipAddress"/><BR/>  
        <xsl:value-of select="ShipCity"/>, <xsl:value-of select="ShipRegion"/>  <xsl:value-of select="ShipPostalCode"/><BR/>  
        <xsl:value-of select="ShipCountry"/></TD></TR>  
  </TABLE>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 Poniższy kod wypełnia **zestaw danych** i stosuje arkusz stylów XSLT.  
  
> [!NOTE]
> Jeśli stosujesz arkusz stylów XSLT do **zestawu danych** , który zawiera relacje, osiągasz najlepszą wydajność, jeśli ustawisz właściwość **zagnieżdżoną** <xref:System.Data.DataRelation> na **true** dla każdej zagnieżdżonej relacji. Pozwala to na korzystanie z arkuszy stylów XSLT, które implementują naturalne przetwarzanie w dół w celu nawigowania po hierarchii i przekształcania danych, w przeciwieństwie do korzystania z osi lokalizacji XPath intensywnie korzystających z wydajności (na przykład poprzedzający element równorzędny i następujący element w stylu wyrażenia testowe węzła arkusza) do nawigowania. Aby uzyskać więcej informacji na temat relacji zagnieżdżonych, zobacz [zagnieżdżanie relacji](nesting-datarelations.md)danych.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)   
  
Dim xslTran As XslTransform = New XslTransform  
xslTran.Load("transform.xsl")  
  
Dim writer As XmlTextWriter = New XmlTextWriter( _  
  "xslt_output.html", System.Text.Encoding.UTF8)  
  
xslTran.Transform(xmlDoc, Nothing, writer)  
writer.Close()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
DataSet custDS = new DataSet("CustomerDataSet");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(custDS, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(custDS, "Orders");  
  
connection.Close();  
  
custDS.Relations.Add("CustOrders",  
  custDS.Tables["Customers"].Columns["CustomerID"],  
                     custDS.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(custDS);   
  
XslTransform xslTran = new XslTransform();  
xslTran.Load("transform.xsl");  
  
XmlTextWriter writer = new XmlTextWriter("xslt_output.html",   
  System.Text.Encoding.UTF8);  
  
xslTran.Transform(xmlDoc, null, writer);  
writer.Close();  
```  
  
## <a name="see-also"></a>Zobacz także

- [Synchronizacja elementów DataSet i XmlDataDocument](dataset-and-xmldatadocument-synchronization.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
