---
title: Stosowanie transformacji XSLT do zestawu danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09f2e4ee-1d08-4ba8-8936-83394fee319d
ms.openlocfilehash: b665fc9593cd73e759625bdfd537581958f8734d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595568"
---
# <a name="applying-an-xslt-transform-to-a-dataset"></a><span data-ttu-id="e6940-102">Stosowanie transformacji XSLT do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="e6940-102">Applying an XSLT Transform to a DataSet</span></span>
<span data-ttu-id="e6940-103">**WriteXml** metody <xref:System.Data.DataSet> umożliwia zapisanie zawartości **DataSet** jako danych XML.</span><span class="sxs-lookup"><span data-stu-id="e6940-103">The **WriteXml** method of the <xref:System.Data.DataSet> enables you to write the contents of a **DataSet** as XML data.</span></span> <span data-ttu-id="e6940-104">Często wykonywanym zadaniem jest następnie Przekształć element XML, że na inny format za pomocą przekształcenia XSL (XSLT).</span><span class="sxs-lookup"><span data-stu-id="e6940-104">A common task is to then transform that XML to another format using XSL transformations (XSLT).</span></span> <span data-ttu-id="e6940-105">Jednak synchronizowanie **zestawu danych** z <xref:System.Xml.XmlDataDocument> umożliwia zastosowanie arkusz stylów XSLT do zawartości **DataSet** bez konieczności pisania najpierw zawartość  **Zestaw danych** jako danych XML przy użyciu **WriteXml**.</span><span class="sxs-lookup"><span data-stu-id="e6940-105">However, synchronizing a **DataSet** with an <xref:System.Xml.XmlDataDocument> enables you to apply an XSLT stylesheet to the contents of a **DataSet** without having to first write the contents of the **DataSet** as XML data using **WriteXml**.</span></span>  
  
 <span data-ttu-id="e6940-106">W poniższym przykładzie **zestawu danych** tabele i relacje, synchronizuje **DataSet** z **XmlDataDocument**i zapisuje część  **Zestaw danych** jako kodu HTML, plików, przy użyciu arkusz stylów XSLT.</span><span class="sxs-lookup"><span data-stu-id="e6940-106">The following example populates a **DataSet** with tables and relationships, synchronizes the **DataSet** with an **XmlDataDocument**, and writes a portion of the **DataSet** as an HTML file using an XSLT stylesheet.</span></span> <span data-ttu-id="e6940-107">Poniżej przedstawiono zawartość arkusza stylów XSLT.</span><span class="sxs-lookup"><span data-stu-id="e6940-107">Following are the contents of the XSLT stylesheet.</span></span>  
  
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
  
 <span data-ttu-id="e6940-108">Poniższy kod wypełnienia **DataSet** i stosuje arkusz stylów XSLT.</span><span class="sxs-lookup"><span data-stu-id="e6940-108">The following code fills the **DataSet** and applies the XSLT style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6940-109">Jeśli chcesz zastosować arkusz stylów XSLT do **DataSet** zawierającą relacji, osiągnąć najlepszą wydajność, jeśli ustawisz **zagnieżdżone** właściwość <xref:System.Data.DataRelation> do **true**dla każdego zagnieżdżone relacji.</span><span class="sxs-lookup"><span data-stu-id="e6940-109">If you are applying an XSLT style sheet to a **DataSet** that contains relations, you achieve best performance if you set the **Nested** property of the <xref:System.Data.DataRelation> to **true** for each nested relation.</span></span> <span data-ttu-id="e6940-110">Dzięki temu można używać arkuszy stylów XSLT Implementowanie przetworzenia góra dół fizycznych można nawigować po hierarchii i przekształcać dane, w przeciwieństwie do używania intensywnie XPath lokalizacji osi (na przykład poprzedni element równorzędny i następujący element równorzędny w stylu Arkusz test wyrażenia węzła) aby nawigować po nim.</span><span class="sxs-lookup"><span data-stu-id="e6940-110">This allows you to use XSLT style sheets that implement natural top-down processing to navigate the hierarchy and transform the data, as opposed to using performance-intensive XPath location axes (for example, preceding-sibling and following-sibling in style sheet node test expressions) to navigate it.</span></span> <span data-ttu-id="e6940-111">Aby uzyskać więcej informacji dotyczących zagnieżdżonych relacji, zobacz [zagnieżdżanie elementów DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="e6940-111">For more information on nested relations, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6940-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6940-112">See also</span></span>
- [<span data-ttu-id="e6940-113">Synchronizacja elementów DataSet i XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="e6940-113">DataSet and XmlDataDocument Synchronization</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)
- [<span data-ttu-id="e6940-114">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="e6940-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
