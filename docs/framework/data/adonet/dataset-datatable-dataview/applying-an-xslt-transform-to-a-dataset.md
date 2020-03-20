---
title: Stosowanie transformacji XSLT do elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09f2e4ee-1d08-4ba8-8936-83394fee319d
ms.openlocfilehash: 3f066f29b99ade6e92a263110fed8079208567b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151497"
---
# <a name="applying-an-xslt-transform-to-a-dataset"></a>Stosowanie transformacji XSLT do elementu DataSet

**Metoda WriteXml** <xref:System.Data.DataSet> umożliwia zapisanie zawartości zestawu **danych** jako danych XML. Typowym zadaniem jest przekształcenie tego pliku XML w inny format przy użyciu przekształceń XSL (XSLT). Jednak synchronizacja **zestawu danych** <xref:System.Xml.XmlDataDocument> z elementem umożliwia zastosowanie arkusza stylów XSLT do zawartości **zestawu danych** bez konieczności uprzedniego zapisania zawartości **zestawu danych** jako danych XML przy użyciu **pliku WriteXml**.  
  
 Poniższy przykład wypełnia **zestaw danych** tabelami i relacjami, synchronizuje **zestaw danych** z **dokumentem XmlDataDocument**i zapisuje część **zestawu danych** jako plik HTML przy użyciu arkusza stylów XSLT. Poniżej przedstawiono zawartość arkusza stylów XSLT:
  
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
> Jeśli stosujesz arkusz stylów XSLT do **zestawu danych** zawierającego relacje, uzyskasz najlepszą wydajność, jeśli ustawisz właściwość **Zagnieżdżona** <xref:System.Data.DataRelation> na **true** dla każdej relacji zagnieżdżonej. Dzięki temu można używać arkuszy stylów XSLT, które implementują naturalne przetwarzanie od góry do do dolnych, aby poruszać się po hierarchii i przekształcać dane, w przeciwieństwie do używania osi lokalizacji XPath o dużej wydajności (na przykład poprzedniego rodzeństwa i następującego rodzeństwa w stylu wyrażenia testowe węzła arkusza), aby poruszać się po nim. Aby uzyskać więcej informacji na temat zagnieżdżonych relacji, zobacz [Zagnieżdżanie danych .](nesting-datarelations.md)  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Synchronizacja elementów DataSet i XmlDataDocument](dataset-and-xmldatadocument-synchronization.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
