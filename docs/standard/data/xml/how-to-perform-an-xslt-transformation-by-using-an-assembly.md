---
title: 'Instrukcje: wykonywanie transformacji XSLT przy użyciu zestawu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76ee440b-d134-4f8f-8262-b917ad6dcbf6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e998526f3e5fcefdf6b776fb493cf9625e6c696
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957144"
---
# <a name="how-to-perform-an-xslt-transformation-by-using-an-assembly"></a>Instrukcje: wykonywanie transformacji XSLT przy użyciu zestawu
Kompilator XSLT (xsltc. exe) kompiluje arkusze stylów XSLT i generuje zestaw. Zestaw można przesłać bezpośrednio do metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType>.  
  
### <a name="to-copy-the-xml-and-xslt-files-to-your-local-computer"></a>Aby skopiować pliki XML i XSLT na komputer lokalny  
  
- Skopiuj plik XSLT na komputer lokalny i nadaj mu nazwę Transform. xsl.  
  
    ```xml  
    <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
      xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
      xmlns:user="urn:my-scripts">  
      <msxsl:script language="C#" implements-prefix="user">  
        <![CDATA[  
      public string discount(string price){  
        char[] trimChars = { '$' };  
        //trim leading $, convert price to type double  
        double discount_value = Convert.ToDouble(price.TrimStart(trimChars));  
        //apply 10% discount and round appropriately  
        discount_value = .9*discount_value;  
        //convert value to decimal and format as currency  
        string discount_price = discount_value.ToString("C");  
        return discount_price;  
      }  
      ]]>  
      </msxsl:script>  
      <xsl:template match="catalog">  
        <html>  
          <head></head>  
          <body>  
            <table border="1">  
              <tr>  
                <th align="left">Title</th>  
                <th align="left">Author</th>  
                <th align="left">Genre</th>  
                <th align="left">Publish Date</th>  
                <th align="left">Price</th>  
              </tr>  
              <xsl:for-each select="book">  
                <tr>  
                  <td>  
                    <xsl:value-of select="title"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="author"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="genre"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="publish_date"/>  
                  </td>  
                  <xsl:choose>  
                    <xsl:when test="genre = 'Fantasy'">  
                      <td>  
                        <xsl:value-of select="user:discount(price)"/>  
                      </td>  
                    </xsl:when>  
                    <xsl:otherwise>  
                      <td>  
                        <xsl:value-of select="price"/>  
                      </td>  
                    </xsl:otherwise>  
                  </xsl:choose>  
                </tr>  
              </xsl:for-each>  
            </table>  
          </body>  
        </html>  
      </xsl:template>  
    </xsl:stylesheet>  
    ```  
  
- Skopiuj plik XML na komputer lokalny i nadaj mu nazwę `books.xml`.  
  
    ```xml  
    <?xml version="1.0"?>  
    <catalog>  
       <book id="bk101">  
          <author>Gambardella, Matthew</author>  
          <title>XML Developer's Guide</title>  
          <genre>Computer</genre>  
          <price>$44.95</price>  
          <publish_date>2000-10-01</publish_date>  
       </book>  
       <book id="bk102">  
          <author>Ralls, Kim</author>  
          <title>Midnight Rain</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-12-16</publish_date>  
       </book>  
       <book id="bk103">  
          <author>Corets, Eva</author>  
          <title>Maeve Ascendant</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-11-17</publish_date>  
       </book>  
       <book id="bk106">  
          <author>Randall, Cynthia</author>  
          <title>Lover Birds</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-09-02</publish_date>  
       </book>  
       <book id="bk107">  
          <author>Thurman, Paula</author>  
          <title>Splish Splash</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-11-02</publish_date>  
       </book>  
    </catalog>  
    ```  
  
### <a name="to-compile-the-style-sheet-with-the-script-enabled"></a>Aby skompilować arkusz stylów z włączonym skryptem.  
  
1. Wykonanie następującego polecenia w wierszu polecenia powoduje utworzenie dwóch zestawów o nazwach `Transform.dll` i `Transform_Script1.dll` (jest to zachowanie domyślne. O ile nie określono inaczej, nazwa klasy i zestawu domyślnie jest nazwą arkusza stylów głównych):  
  
    ```console  
    xsltc /settings:script+ Transform.xsl  
    ```
  
    Następujące polecenie jawnie ustawia nazwę klasy do przekształcenia:  
  
    ```console  
    xsltc /settings:script+ /class:Transform Transform.xsl  
    ```  
  
### <a name="to-include-the-compiled-assembly-as-a-reference-when-you-compile-your-code"></a>W celu uwzględnienia skompilowanego zestawu jako odwołania podczas kompilowania kodu.  
  
1. Możesz dołączyć zestaw w programie Visual Studio, dodając odwołanie w Eksplorator rozwiązań lub z wiersza polecenia.  
  
2. W wierszu polecenia w programie C#należy użyć następujących poleceń:  
  
    ```console  
    csc myCode.cs /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
3. Dla wiersza polecenia z Visual Basic Użyj następujących poleceń:  
  
    ```console  
    vbc myCode.vb /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
### <a name="to-use-the-compiled-assembly-in-your-code"></a>Aby użyć skompilowanego zestawu w kodzie.  
  
Poniższy przykład pokazuje, jak wykonać transformację XSLT przy użyciu skompilowanego arkusza stylów.  
  
[!code-csharp[XslTransform_XSLTC#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslTransform_XSLTC/CS/XslTransform_XSLTC.cs#1)]
[!code-vb[XslTransform_XSLTC#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslTransform_XSLTC/VB/XslTransform_XSLTC.vb#1)]  
  
Aby dynamicznie połączyć się z skompilowanym zestawem, Zastąp
  
```csharp  
xslt.Load(typeof(Transform));  
```  
  
with  
  
```csharp 
xslt.Load(System.Reflection.Assembly.Load("Transform").GetType("Transform"));  
``` 
  
w powyższym przykładzie. Aby uzyskać więcej informacji na temat metody Assembly. Load, zobacz <xref:System.Reflection.Assembly.Load%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [Kompilator XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)
- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
