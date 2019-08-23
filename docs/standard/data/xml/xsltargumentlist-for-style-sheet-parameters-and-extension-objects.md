---
title: Klasa XsltArgumentList — parametry arkusza stylów i obiekty rozszerzeń
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d08399933f37c4110639bf1f4a81f222dd597b4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910323"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a><span data-ttu-id="72e75-102">Klasa XsltArgumentList — parametry arkusza stylów i obiekty rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="72e75-102">XsltArgumentList for Style Sheet Parameters and Extension Objects</span></span>
<span data-ttu-id="72e75-103"><xref:System.Xml.Xsl.XsltArgumentList> Klasa zawiera Extensible Stylesheet Language dla parametrów Transformations (XSLT) i obiektów rozszerzeń XSLT.</span><span class="sxs-lookup"><span data-stu-id="72e75-103">The <xref:System.Xml.Xsl.XsltArgumentList> class contains Extensible Stylesheet Language for Transformations (XSLT) parameters and XSLT extension objects.</span></span> <span data-ttu-id="72e75-104">Po przekazaniu <xref:System.Xml.Xsl.XslTransform.Transform%2A> do metody te parametry i obiekty rozszerzeń mogą być wywoływane z arkuszy stylów.</span><span class="sxs-lookup"><span data-stu-id="72e75-104">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72e75-105">Klasy <xref:System.Xml.Xsl.XslTransform> i<xref:System.Xml.Xsl.XsltArgumentList> są przestarzałe w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="72e75-105">The <xref:System.Xml.Xsl.XslTransform> and <xref:System.Xml.Xsl.XsltArgumentList> classes are obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="72e75-106">Przekształcenia XSLT można wykonywać przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="72e75-106">You can perform XSLT transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="72e75-107">Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="72e75-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="72e75-108"><xref:System.Xml.Xsl.XsltArgumentList> Klasa zawiera parametry XSLT i obiekty rozszerzeń XSLT.</span><span class="sxs-lookup"><span data-stu-id="72e75-108">The <xref:System.Xml.Xsl.XsltArgumentList> class contains XSLT parameters and XSLT extension objects.</span></span> <span data-ttu-id="72e75-109">Po przekazaniu <xref:System.Xml.Xsl.XslTransform.Transform%2A> do metody te parametry i obiekty rozszerzeń mogą być wywoływane z arkuszy stylów.</span><span class="sxs-lookup"><span data-stu-id="72e75-109">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
 <span data-ttu-id="72e75-110">Poniżej przedstawiono zalety przekazywania obiektów zamiast używać osadzonego skryptu:</span><span class="sxs-lookup"><span data-stu-id="72e75-110">The following are advantages to passing an object rather than using an embedded script:</span></span>  
  
- <span data-ttu-id="72e75-111">Zapewnia lepszą hermetyzację i ponowne użycie klas.</span><span class="sxs-lookup"><span data-stu-id="72e75-111">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="72e75-112">Zezwala na mniejsze i łatwiejsze w obsłudze arkusze stylów.</span><span class="sxs-lookup"><span data-stu-id="72e75-112">Allows style sheets to be smaller and more maintainable.</span></span>  
  
- <span data-ttu-id="72e75-113">Obsługuje metody wywoływania w klasach należących do przestrzeni nazw innych niż te zdefiniowane w ramach <xref:System> zestawu obsługiwanych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="72e75-113">Supports calling methods on classes belonging to namespaces other than those defined within the set of supported <xref:System> namespaces.</span></span>  
  
- <span data-ttu-id="72e75-114">Obsługuje przekazywanie fragmentów drzewa wyników do arkusza stylów przy użyciu <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="72e75-114">Supports passing result tree fragments to the style sheet with the use of the <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
## <a name="xslt-style-sheet-parameters"></a><span data-ttu-id="72e75-115">Parametry arkusza stylów XSLT</span><span class="sxs-lookup"><span data-stu-id="72e75-115">XSLT Style Sheet Parameters</span></span>  
 <span data-ttu-id="72e75-116">Parametry XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody using.</span><span class="sxs-lookup"><span data-stu-id="72e75-116">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="72e75-117">Kwalifikowana nazwa i przestrzeń nazw Uniform Resource Identifier (URI) są skojarzone z obiektem parametru w tym czasie.</span><span class="sxs-lookup"><span data-stu-id="72e75-117">A qualified name and namespace Uniform Resource Identifier (URI) are associated with the parameter object at that time.</span></span>  
  
 <span data-ttu-id="72e75-118">Obiekt parametru powinien odpowiadać typowi organizacja World Wide Web Consortium (W3C).</span><span class="sxs-lookup"><span data-stu-id="72e75-118">The parameter object should correspond to a World Wide Web Consortium (W3C) type.</span></span> <span data-ttu-id="72e75-119">W poniższej tabeli przedstawiono odpowiednie typy W3C, równoważne klasy .NET Framework (typ) i określające, czy typem W3C jest typ języka ścieżki XML (XPath) czy typ XSLT.</span><span class="sxs-lookup"><span data-stu-id="72e75-119">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (type), and whether the W3C type is an XML Path Language (XPath) type or XSLT type.</span></span>  
  
|<span data-ttu-id="72e75-120">Typ W3C</span><span class="sxs-lookup"><span data-stu-id="72e75-120">W3C Type</span></span>|<span data-ttu-id="72e75-121">Równoważna Klasa .NET Framework (typ)</span><span class="sxs-lookup"><span data-stu-id="72e75-121">Equivalent .NET Framework class (type)</span></span>|<span data-ttu-id="72e75-122">Typ XPath lub typ XSLT</span><span class="sxs-lookup"><span data-stu-id="72e75-122">XPath type or XSLT type</span></span>|  
|--------------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="72e75-123">String</span><span class="sxs-lookup"><span data-stu-id="72e75-123">String</span></span>|<span data-ttu-id="72e75-124">System.String</span><span class="sxs-lookup"><span data-stu-id="72e75-124">System.String</span></span>|<span data-ttu-id="72e75-125">XPath</span><span class="sxs-lookup"><span data-stu-id="72e75-125">XPath</span></span>|  
|<span data-ttu-id="72e75-126">Boolean</span><span class="sxs-lookup"><span data-stu-id="72e75-126">Boolean</span></span>|<span data-ttu-id="72e75-127">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="72e75-127">System.Boolean</span></span>|<span data-ttu-id="72e75-128">XPath</span><span class="sxs-lookup"><span data-stu-id="72e75-128">XPath</span></span>|  
|<span data-ttu-id="72e75-129">Wartość liczbowa</span><span class="sxs-lookup"><span data-stu-id="72e75-129">Number</span></span>|<span data-ttu-id="72e75-130">System.Double</span><span class="sxs-lookup"><span data-stu-id="72e75-130">System.Double</span></span>|<span data-ttu-id="72e75-131">XPath</span><span class="sxs-lookup"><span data-stu-id="72e75-131">XPath</span></span>|  
|<span data-ttu-id="72e75-132">Fragment drzewa wyników</span><span class="sxs-lookup"><span data-stu-id="72e75-132">Result Tree Fragment</span></span>|<span data-ttu-id="72e75-133">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="72e75-133">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="72e75-134">XSLT</span><span class="sxs-lookup"><span data-stu-id="72e75-134">XSLT</span></span>|  
|<span data-ttu-id="72e75-135">Zestaw węzłów</span><span class="sxs-lookup"><span data-stu-id="72e75-135">Node Set</span></span>|<span data-ttu-id="72e75-136">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="72e75-136">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="72e75-137">XPath</span><span class="sxs-lookup"><span data-stu-id="72e75-137">XPath</span></span>|  
  
 <span data-ttu-id="72e75-138">Jeśli obiekt parametru nie jest jedną z powyższych klas, wymuszony jest podwójny lub ciąg, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="72e75-138">If the parameter object is not one of the above classes, it is forced to either a Double or String, as appropriate.</span></span> <span data-ttu-id="72e75-139">Wartości Int16, UInt16, Int32, UInt32, Int64, UInt64, Single i Decimal są wymuszane jako Double.</span><span class="sxs-lookup"><span data-stu-id="72e75-139">Int16, UInt16, Int32, UInt32, Int64, UInt64, Single and Decimal types are forced to a Double.</span></span> <span data-ttu-id="72e75-140">Wszystkie inne typy są wymuszane jako ciąg za pomocą `ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="72e75-140">All other types are forced to a String using the `ToString` method.</span></span>  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a><span data-ttu-id="72e75-141">Aby użyć parametru XSLT, użytkownik musi wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="72e75-141">To use the XSLT parameter, the user needs to do the following:</span></span>  
  
1. <span data-ttu-id="72e75-142">Utwórz i Dodaj obiekty przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>. <xref:System.Xml.Xsl.XsltArgumentList></span><span class="sxs-lookup"><span data-stu-id="72e75-142">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the objects using <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span></span>  
  
2. <span data-ttu-id="72e75-143">Wywołaj parametry z arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="72e75-143">Call the parameters from the style sheet.</span></span>  
  
3. <span data-ttu-id="72e75-144"><xref:System.Xml.Xsl.XsltArgumentList> Przekaż<xref:System.Xml.Xsl.XslTransform.Transform%2A> do metody.</span><span class="sxs-lookup"><span data-stu-id="72e75-144">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="72e75-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="72e75-145">Example</span></span>  
 <span data-ttu-id="72e75-146">W poniższym przykładzie zastosowano <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metodę, aby utworzyć parametr do przechowywania obliczonej daty rabatu.</span><span class="sxs-lookup"><span data-stu-id="72e75-146">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold a calculated discount date.</span></span> <span data-ttu-id="72e75-147">Data rabatu jest obliczana na 20 dni od daty zamówienia.</span><span class="sxs-lookup"><span data-stu-id="72e75-147">The discount date is calculated to be 20 days from the order date.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public class Sample  
  
   Private Const filename As String = "order.xml"  
   Private Const stylesheet As String = "discount.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Calculate the discount date.  
    Dim today As DateTime = DateTime.Now  
    Dim d As DateTime = today.AddDays(20)  
    xslArg.AddParam("discount", "", d.ToString())  
  
    'Create an XmlTextWriter to handle the output.  
    Dim writer As XmlTextWriter = New XmlTextWriter("orderout.xml", Nothing)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
  
    writer.Close()  
  
  End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "order.xml";  
   private const String stylesheet = "discount.xsl";  
  
   public static void Main() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Calculate the discount date.  
    DateTime today = DateTime.Now;  
    DateTime d = today.AddDays(20);  
    xslArg.AddParam("discount", "", d.ToString());  
  
    //Create an XmlTextWriter to handle the output.  
    XmlTextWriter writer = new XmlTextWriter("orderout.xml", null);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="72e75-148">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="72e75-148">Input</span></span>  
 <span data-ttu-id="72e75-149">order.xml</span><span class="sxs-lookup"><span data-stu-id="72e75-149">order.xml</span></span>  
  
```xml  
<!--Represents a customer order-->  
<order>  
  <book ISBN='10-861003-324'>  
    <title>The Handmaid's Tale</title>  
    <price>19.95</price>  
  </book>  
  <cd ISBN='2-3631-4'>  
    <title>Americana</title>  
    <price>16.95</price>  
  </cd>  
</order>  
```  
  
 <span data-ttu-id="72e75-150">Discount. xsl</span><span class="sxs-lookup"><span data-stu-id="72e75-150">discount.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:param name="discount"/>  
  <xsl:template match="/">  
    <order>  
      <xsl:variable name="sub-total" select="sum(//price)"/>  
      <total><xsl:value-of select="$sub-total"/></total>  
      15% discount if paid by: <xsl:value-of select="$discount"/>  
    </order>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a><span data-ttu-id="72e75-151">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="72e75-151">Output</span></span>  
  
```xml  
<order>  
   <total>36.9</total>   
   15% discount if paid by: 5/6/2001 5:01:15 PM   
</order>  
```  
  
## <a name="xslt-extension-objects"></a><span data-ttu-id="72e75-152">Obiekty rozszerzeń XSLT</span><span class="sxs-lookup"><span data-stu-id="72e75-152">XSLT Extension Objects</span></span>  
 <span data-ttu-id="72e75-153">Obiekty rozszerzeń XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody using.</span><span class="sxs-lookup"><span data-stu-id="72e75-153">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="72e75-154">Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektem rozszerzenia w tym czasie.</span><span class="sxs-lookup"><span data-stu-id="72e75-154">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
 <span data-ttu-id="72e75-155">Po dodaniu obiektu obiekt wywołujący <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> musi być w pełni zaufany w zasadach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="72e75-155">When an object is added, the caller of the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> must be fully trusted in the security policy.</span></span> <span data-ttu-id="72e75-156">Jeśli obiekt wywołujący jest częściowo zaufany, dodanie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="72e75-156">If the caller is semi-trusted, the addition will fail.</span></span>  
  
 <span data-ttu-id="72e75-157">Mimo że obiekt został pomyślnie dodany, nie gwarantuje to, że wykonywanie zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="72e75-157">Though an object is added successfully, it does not guarantee that the execution will be successful.</span></span> <span data-ttu-id="72e75-158">Gdy metoda jest wywoływana, uprawnienia są obliczane na podstawie dowodów dostarczonych w <xref:System.Xml.Xsl.XslTransform.Load%2A> czasie, a zestaw uprawnień jest przypisany do całego procesu transformacji. <xref:System.Xml.Xsl.XslTransform.Transform%2A></span><span class="sxs-lookup"><span data-stu-id="72e75-158">When the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is called, permissions are calculated against the evidence provided at <xref:System.Xml.Xsl.XslTransform.Load%2A> time, and that permission set is assigned to the entire transformation process.</span></span> <span data-ttu-id="72e75-159">Jeśli obiekt rozszerzenia próbuje zainicjować akcję, która wymaga uprawnień nieznalezionych w zestawie, zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="72e75-159">If an extension object attempts to initiate an action that requires permissions not found in the set, an exception is thrown.</span></span>  
  
 <span data-ttu-id="72e75-160">Typy danych zwracane z obiektów rozszerzeń to jeden z czterech podstawowych typów danych XPath o liczbie, ciągu, wartości logicznej i zestawie węzłów.</span><span class="sxs-lookup"><span data-stu-id="72e75-160">The data types returned from extension objects are one of the four basic XPath data types of number, string, Boolean, and node set.</span></span>  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a><span data-ttu-id="72e75-161">Aby użyć obiektu rozszerzenia XSLT, użytkownik musi wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="72e75-161">To use the XSLT extension object, the user needs to do the following:</span></span>  
  
1. <span data-ttu-id="72e75-162">Utwórz i Dodaj obiekt rozszerzenia przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>. <xref:System.Xml.Xsl.XsltArgumentList></span><span class="sxs-lookup"><span data-stu-id="72e75-162">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span></span>  
  
2. <span data-ttu-id="72e75-163">Wywołaj obiekt rozszerzenia z arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="72e75-163">Invoke the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="72e75-164"><xref:System.Xml.Xsl.XsltArgumentList> Przekaż<xref:System.Xml.Xsl.XslTransform.Transform%2A> do metody.</span><span class="sxs-lookup"><span data-stu-id="72e75-164">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="72e75-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="72e75-165">Example</span></span>  
 <span data-ttu-id="72e75-166">Poniższy przykład oblicza obwód okręgu, w którym znajduje się jego promień.</span><span class="sxs-lookup"><span data-stu-id="72e75-166">The following example calculates the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "circle.xsl"  
  
   Public Shared Sub Main()  
        Dim test As Sample = New Sample  
   End Sub  
  
  Public Sub New()  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Add an object to calculate the circumference of the circle.  
    Dim obj As Calculate = New Calculate  
    xslArg.AddExtensionObject("urn:myObj", obj)  
  
    'Create an XmlTextWriter to output to the console.  
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
    writer.Close()  
  
  End Sub  
  
  'Calculates the circumference of a circle given the radius.  
  Public Class Calculate  
  
    Private circ As double = 0  
  
    Public Function Circumference(radius As Double) As Double  
       circ = Math.PI*2*radius  
       Return circ  
    End Function  
  End Class  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "circle.xsl";  
  
   public static void Main() {  
  
        Sample test = new Sample();  
    }  
  
  public Sample() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Add an object to calculate the circumference of the circle.  
    Calculate obj = new Calculate();  
    xslArg.AddExtensionObject("urn:myObj", obj);  
  
    //Create an XmlTextWriter to output to the console.  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  
  }  
  
  //Calculates the circumference of a circle given the radius.  
  public class Calculate {  
  
    private double circ = 0;  
  
    public double Circumference(double radius){  
       circ = Math.PI*2*radius;  
       return circ;  
    }  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="72e75-167">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="72e75-167">Input</span></span>  
 <span data-ttu-id="72e75-168">number.xml</span><span class="sxs-lookup"><span data-stu-id="72e75-168">number.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>    
```  
  
 <span data-ttu-id="72e75-169">Circle. xsl</span><span class="sxs-lookup"><span data-stu-id="72e75-169">circle.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:myObj="urn:myObj">  
  
  <xsl:template match="data">  
  <circles>  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="myObj:Circumference(radius)"/>          
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a><span data-ttu-id="72e75-170">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="72e75-170">Output</span></span>  
 `<circles xmlns:myObj="urn:myObj">`  
  
 `<circle>`  
  
 `<radius>12</radius>`  
  
 `<circumference>75.398223686155</circumference>`  
  
 `</circle>`  
  
 `<circle>`  
  
 `<radius>37.5</radius>`  
  
 `<circumference>235.61944901923448</circumference>`  
  
 `</circle>`  
  
 `</circles>`  
  
## <a name="see-also"></a><span data-ttu-id="72e75-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72e75-171">See also</span></span>

- [<span data-ttu-id="72e75-172">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="72e75-172">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
