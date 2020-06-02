---
title: 'Instrukcje: Wykonywanie przekształcenia XSLT przy użyciu zestawu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76ee440b-d134-4f8f-8262-b917ad6dcbf6
ms.openlocfilehash: 623f997d1c11bc643ea4605614cac147b6069be5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287730"
---
# <a name="how-to-perform-an-xslt-transformation-by-using-an-assembly"></a><span data-ttu-id="40363-102">Instrukcje: Wykonywanie przekształcenia XSLT przy użyciu zestawu</span><span class="sxs-lookup"><span data-stu-id="40363-102">How to: Perform an XSLT Transformation by Using an Assembly</span></span>
<span data-ttu-id="40363-103">Kompilator XSLT (xsltc. exe) kompiluje arkusze stylów XSLT i generuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="40363-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="40363-104">Zestaw można przesłać bezpośrednio do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="40363-104">The assembly can be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-copy-the-xml-and-xslt-files-to-your-local-computer"></a><span data-ttu-id="40363-105">Aby skopiować pliki XML i XSLT na komputer lokalny</span><span class="sxs-lookup"><span data-stu-id="40363-105">To copy the XML and XSLT files to your local computer</span></span>  
  
- <span data-ttu-id="40363-106">Skopiuj plik XSLT na komputer lokalny i nadaj mu nazwę Transform. xsl.</span><span class="sxs-lookup"><span data-stu-id="40363-106">Copy the XSLT file to your local computer and name it Transform.xsl.</span></span>  
  
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
  
- <span data-ttu-id="40363-107">Skopiuj plik XML na komputer lokalny i nadaj mu nazwę `books.xml` .</span><span class="sxs-lookup"><span data-stu-id="40363-107">Copy the XML file to your local computer and name it `books.xml`.</span></span>  
  
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
  
### <a name="to-compile-the-style-sheet-with-the-script-enabled"></a><span data-ttu-id="40363-108">Aby skompilować arkusz stylów z włączonym skryptem.</span><span class="sxs-lookup"><span data-stu-id="40363-108">To compile the style sheet with the script enabled.</span></span>  
  
1. <span data-ttu-id="40363-109">Wykonanie następującego polecenia w wierszu polecenia powoduje utworzenie dwóch zestawów o nazwach `Transform.dll` i `Transform_Script1.dll` (jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="40363-109">Executing the following command from the command line creates two assemblies named `Transform.dll` and `Transform_Script1.dll` (This is the default behavior.</span></span> <span data-ttu-id="40363-110">O ile nie określono inaczej, nazwa klasy i zestawu domyślnie jest nazwą arkusza stylów głównych):</span><span class="sxs-lookup"><span data-stu-id="40363-110">Unless otherwise specified, the name of the class and the assembly defaults to the name of the main style sheet):</span></span>  
  
    ```console  
    xsltc /settings:script+ Transform.xsl  
    ```
  
    <span data-ttu-id="40363-111">Następujące polecenie jawnie ustawia nazwę klasy do przekształcenia:</span><span class="sxs-lookup"><span data-stu-id="40363-111">The following command explicitly sets the class name to Transform:</span></span>  
  
    ```console  
    xsltc /settings:script+ /class:Transform Transform.xsl  
    ```  
  
### <a name="to-include-the-compiled-assembly-as-a-reference-when-you-compile-your-code"></a><span data-ttu-id="40363-112">W celu uwzględnienia skompilowanego zestawu jako odwołania podczas kompilowania kodu.</span><span class="sxs-lookup"><span data-stu-id="40363-112">To include the compiled assembly as a reference when you compile your code.</span></span>  
  
1. <span data-ttu-id="40363-113">Możesz dołączyć zestaw w programie Visual Studio, dodając odwołanie w Eksplorator rozwiązań lub z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="40363-113">You can include an assembly in Visual Studio by adding a reference in the Solution Explorer, or from the command line.</span></span>  
  
2. <span data-ttu-id="40363-114">W wierszu polecenia w języku C# wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="40363-114">For the command line with C#, use the following:</span></span>  
  
    ```console  
    csc myCode.cs /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
3. <span data-ttu-id="40363-115">Dla wiersza polecenia z Visual Basic Użyj następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="40363-115">For the command line with Visual Basic, use the following</span></span>  
  
    ```console  
    vbc myCode.vb /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
### <a name="to-use-the-compiled-assembly-in-your-code"></a><span data-ttu-id="40363-116">Aby użyć skompilowanego zestawu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="40363-116">To use the compiled assembly in your code.</span></span>  
  
<span data-ttu-id="40363-117">Poniższy przykład pokazuje, jak wykonać transformację XSLT przy użyciu skompilowanego arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="40363-117">The following example shows how to execute the XSLT transformation by using the compiled style sheet.</span></span>  
  
[!code-csharp[XslTransform_XSLTC#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslTransform_XSLTC/CS/XslTransform_XSLTC.cs#1)]
[!code-vb[XslTransform_XSLTC#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslTransform_XSLTC/VB/XslTransform_XSLTC.vb#1)]  
  
<span data-ttu-id="40363-118">Aby dynamicznie połączyć się z skompilowanym zestawem, Zastąp</span><span class="sxs-lookup"><span data-stu-id="40363-118">To dynamically link to the compiled assembly, replace</span></span>
  
```csharp  
xslt.Load(typeof(Transform));  
```  
  
<span data-ttu-id="40363-119">with</span><span class="sxs-lookup"><span data-stu-id="40363-119">with</span></span>  
  
```csharp
xslt.Load(System.Reflection.Assembly.Load("Transform").GetType("Transform"));  
```
  
<span data-ttu-id="40363-120">w powyższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="40363-120">in the example above.</span></span> <span data-ttu-id="40363-121">Aby uzyskać więcej informacji na temat metody Assembly. Load, zobacz <xref:System.Reflection.Assembly.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="40363-121">For more information on the Assembly.Load method, see <xref:System.Reflection.Assembly.Load%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40363-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40363-122">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="40363-123">Kompilator XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="40363-123">XSLT Compiler (xsltc.exe)</span></span>](xslt-compiler-xsltc-exe.md)
- [<span data-ttu-id="40363-124">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="40363-124">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="40363-125">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="40363-125">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
