---
title: Konwertowanie ciągów na typy danych programu .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5954a580ca9b7f00f6339f70d0df9d20ba96715e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576582"
---
# <a name="converting-strings-to-net-framework-data-types"></a><span data-ttu-id="f1bb2-102">Konwertowanie ciągów na typy danych programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f1bb2-102">Converting Strings to .NET Framework Data Types</span></span>
<span data-ttu-id="f1bb2-103">Do przekonwertowania ciągu na typ danych .NET Framework, należy użyć **obiekt XmlConvert** — metoda, która pasuje do wymagań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f1bb2-103">If you want to convert a string to a .NET Framework data type, use the **XmlConvert** method that fits the application requirements.</span></span> <span data-ttu-id="f1bb2-104">Aby uzyskać listę wszystkich metod konwersji danych dostępne w **obiekt XmlConvert** , zobacz <xref:System.Xml.XmlConvert>.</span><span class="sxs-lookup"><span data-stu-id="f1bb2-104">For a list of all conversion methods available in the **XmlConvert** class, see <xref:System.Xml.XmlConvert>.</span></span>  
  
 <span data-ttu-id="f1bb2-105">Ciąg zwrócony przez **ToString** metoda jest wersję danych, który jest przekazywany w ciągu.</span><span class="sxs-lookup"><span data-stu-id="f1bb2-105">The string returned from the **ToString** method is a string version of the data that is passed in.</span></span> <span data-ttu-id="f1bb2-106">Ponadto istnieje kilka typów .NET Framework, które konwersji, używając **obiekt XmlConvert** klasy jeszcze nie używaj metod w **System.Convert** klasy.</span><span class="sxs-lookup"><span data-stu-id="f1bb2-106">Additionally, there are several .NET Framework types that convert using the **XmlConvert** class yet they do not use the methods in the **System.Convert** class.</span></span> <span data-ttu-id="f1bb2-107">**Obiekt XmlConvert** klasy zgodna ze specyfikacją typu danych schematu XML (XSD) i ma typ, który danych **obiekt XmlConvert** można mapować.</span><span class="sxs-lookup"><span data-stu-id="f1bb2-107">The **XmlConvert** class follows the XML Schema (XSD) data type specification and has a data type that the **XmlConvert** can map to.</span></span>  
  
 <span data-ttu-id="f1bb2-108">W poniższej tabeli wymieniono typy danych .NET Framework i typów ciągów, które są zwracane przy użyciu mapowanie typu danych schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="f1bb2-108">The following table lists .NET Framework data types and the string types that are returned using XML Schema (XSD) data type mapping.</span></span> <span data-ttu-id="f1bb2-109">Nie można przetworzyć tych typów .NET Framework za pomocą **System.Convert**.</span><span class="sxs-lookup"><span data-stu-id="f1bb2-109">These .NET Framework types cannot be processed using **System.Convert**.</span></span>  
  
|<span data-ttu-id="f1bb2-110">Typ programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f1bb2-110">.NET Framework type</span></span>|<span data-ttu-id="f1bb2-111">Zwrócony ciąg</span><span class="sxs-lookup"><span data-stu-id="f1bb2-111">String returned</span></span>|  
|-------------------------|---------------------|  
|<span data-ttu-id="f1bb2-112">Boolean</span><span class="sxs-lookup"><span data-stu-id="f1bb2-112">Boolean</span></span>|<span data-ttu-id="f1bb2-113">"true", "fałsz"</span><span class="sxs-lookup"><span data-stu-id="f1bb2-113">"true", "false"</span></span>|  
|<span data-ttu-id="f1bb2-114">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="f1bb2-114">Single.PositiveInfinity</span></span>|<span data-ttu-id="f1bb2-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="f1bb2-115">"INF"</span></span>|  
|<span data-ttu-id="f1bb2-116">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="f1bb2-116">Single.NegativeInfinity</span></span>|<span data-ttu-id="f1bb2-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="f1bb2-117">"-INF"</span></span>|  
|<span data-ttu-id="f1bb2-118">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="f1bb2-118">Double.PositiveInfinity</span></span>|<span data-ttu-id="f1bb2-119">"INF"</span><span class="sxs-lookup"><span data-stu-id="f1bb2-119">"INF"</span></span>|  
|<span data-ttu-id="f1bb2-120">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="f1bb2-120">Double.NegativeInfinity</span></span>|<span data-ttu-id="f1bb2-121">"-INF"</span><span class="sxs-lookup"><span data-stu-id="f1bb2-121">"-INF"</span></span>|  
|<span data-ttu-id="f1bb2-122">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="f1bb2-122">DateTime</span></span>|<span data-ttu-id="f1bb2-123">Format to "RRRR-MM-ddTHH:mm:sszzzzzz" i jego podzestawy.</span><span class="sxs-lookup"><span data-stu-id="f1bb2-123">Format is "yyyy-MM-ddTHH:mm:sszzzzzz" and its subsets.</span></span>|  
|<span data-ttu-id="f1bb2-124">Zakres czasu</span><span class="sxs-lookup"><span data-stu-id="f1bb2-124">Timespan</span></span>|<span data-ttu-id="f1bb2-125">Format jest PnYnMnTnHnMnS czyli `P2Y10M15DT10H30M20S` jest równa 2 lata, 10 miesięcy, 15 dni, 10 godzin, 30 minut, i 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="f1bb2-125">Format is PnYnMnTnHnMnS that is, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10 hours, 30 minutes, and 20 seconds.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="f1bb2-126">Jeśli konwertowanie dowolnego typu .NET Framework wymieniony w tabeli, aby parametry za pomocą **ToString** metody, zwracany ciąg nie jest typu podstawowego, ale typ ciągu schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="f1bb2-126">If converting any of the .NET Framework types listed in the table to a string using the **ToString** method, the returned string is not the base type, but the XML Schema (XSD) string type.</span></span>  
  
 <span data-ttu-id="f1bb2-127">**DateTime** i **Timespan** typ wartości różni się w tym **DateTime** reprezentuje moment w czasie, podczas gdy **TimeSpan** reprezentuje przedział czasu.</span><span class="sxs-lookup"><span data-stu-id="f1bb2-127">The **DateTime** and **Timespan** value type differs in that a **DateTime** represents an instant in time, whereas a **TimeSpan** represents a time interval.</span></span> <span data-ttu-id="f1bb2-128">**DateTime** i **Timespan** formaty są określone w specyfikacji typów danych schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="f1bb2-128">The **DateTime** and **Timespan** formats are specified in the XML Schema (XSD) data types specification.</span></span> <span data-ttu-id="f1bb2-129">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f1bb2-129">For example:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim [date] As New DateTime(2001, 8, 4)  
writer.WriteElementString("Date", XmlConvert.ToString([date]))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
DateTime date = new DateTime (2001, 08, 04);  
writer.WriteElementString("Date", XmlConvert.ToString(date));  
```  
  
 <span data-ttu-id="f1bb2-130">**Output**</span><span class="sxs-lookup"><span data-stu-id="f1bb2-130">**Output**</span></span>  
  
 <span data-ttu-id="f1bb2-131">`<Date>2001-08-04T00:00:00</Date>`.</span><span class="sxs-lookup"><span data-stu-id="f1bb2-131">`<Date>2001-08-04T00:00:00</Date>`.</span></span>  
  
 <span data-ttu-id="f1bb2-132">Poniższy kod konwertuje całkowitą na ciąg:</span><span class="sxs-lookup"><span data-stu-id="f1bb2-132">The following code converts an integer to a string:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim value As Int32 = 200  
writer.WriteElementString("Number", XmlConvert.ToString(value))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
Int32 value = 200;  
writer.WriteElementString("Number", XmlConvert.ToString(value));  
```  
  
 <span data-ttu-id="f1bb2-133">**Output**</span><span class="sxs-lookup"><span data-stu-id="f1bb2-133">**Output**</span></span>  
  
 `<Number>200</Number>`  
  
 <span data-ttu-id="f1bb2-134">Jednak jeśli konwertowania ciągu na **logiczna**, **pojedynczego**, lub **podwójne**, zwraca typ .NET Framework nie jest taki sam jak typ zwracany po użyciu **System.Convert** klasy.</span><span class="sxs-lookup"><span data-stu-id="f1bb2-134">However, if you are converting a string to **Boolean**, **Single**, or **Double**, the .NET Framework type that is returned is not the same as the type returned when using the **System.Convert** class.</span></span>  
  
## <a name="string-to-boolean"></a><span data-ttu-id="f1bb2-135">Ciąg na wartość logiczną</span><span class="sxs-lookup"><span data-stu-id="f1bb2-135">String to Boolean</span></span>  
 <span data-ttu-id="f1bb2-136">W poniższej tabeli przedstawiono, jakiego typu jest generowane dla danego ciągów wejściowych podczas konwertowania ciągu na **logiczna** przy użyciu **ToBoolean** metody.</span><span class="sxs-lookup"><span data-stu-id="f1bb2-136">The following table shows what type is generated for the given input strings, when converting a string to **Boolean** using the **ToBoolean** method.</span></span>  
  
|<span data-ttu-id="f1bb2-137">Parametr wejściowy prawidłowy ciąg</span><span class="sxs-lookup"><span data-stu-id="f1bb2-137">Valid string input parameter</span></span>|<span data-ttu-id="f1bb2-138">Typ danych wyjściowych .NET framework</span><span class="sxs-lookup"><span data-stu-id="f1bb2-138">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="f1bb2-139">wartość "prawda"</span><span class="sxs-lookup"><span data-stu-id="f1bb2-139">"true"</span></span>|<span data-ttu-id="f1bb2-140">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="f1bb2-140">Boolean.True</span></span>|  
|<span data-ttu-id="f1bb2-141">"1"</span><span class="sxs-lookup"><span data-stu-id="f1bb2-141">"1"</span></span>|<span data-ttu-id="f1bb2-142">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="f1bb2-142">Boolean.True</span></span>|  
|<span data-ttu-id="f1bb2-143">"false"</span><span class="sxs-lookup"><span data-stu-id="f1bb2-143">"false"</span></span>|<span data-ttu-id="f1bb2-144">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="f1bb2-144">Boolean.False</span></span>|  
|<span data-ttu-id="f1bb2-145">„0”</span><span class="sxs-lookup"><span data-stu-id="f1bb2-145">"0"</span></span>|<span data-ttu-id="f1bb2-146">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="f1bb2-146">Boolean.False</span></span>|  
  
 <span data-ttu-id="f1bb2-147">Na przykład podać następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="f1bb2-147">For example, given the following XML:</span></span>  
  
 <span data-ttu-id="f1bb2-148">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="f1bb2-148">**Input**</span></span>  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 <span data-ttu-id="f1bb2-149">Zarówno zostały zrozumiane przez następujący kod i **bDane wartości** jest **System.Boolean.True**:</span><span class="sxs-lookup"><span data-stu-id="f1bb2-149">Both can be understood by the following code, and **bvalue** is **System.Boolean.True**:</span></span>  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a><span data-ttu-id="f1bb2-150">Ciąg do jednego</span><span class="sxs-lookup"><span data-stu-id="f1bb2-150">String to Single</span></span>  
 <span data-ttu-id="f1bb2-151">W poniższej tabeli przedstawiono, jakiego typu jest generowane dla danego ciągów wejściowych podczas konwertowania ciągu na **pojedynczego** przy użyciu **tosingle —** metody.</span><span class="sxs-lookup"><span data-stu-id="f1bb2-151">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToSingle** method.</span></span>  
  
|<span data-ttu-id="f1bb2-152">Parametr wejściowy prawidłowy ciąg</span><span class="sxs-lookup"><span data-stu-id="f1bb2-152">Valid string input parameter</span></span>|<span data-ttu-id="f1bb2-153">Typ danych wyjściowych .NET framework</span><span class="sxs-lookup"><span data-stu-id="f1bb2-153">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="f1bb2-154">"INF"</span><span class="sxs-lookup"><span data-stu-id="f1bb2-154">"INF"</span></span>|<span data-ttu-id="f1bb2-155">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="f1bb2-155">Single.PositiveInfinity</span></span>|  
|<span data-ttu-id="f1bb2-156">"-INF"</span><span class="sxs-lookup"><span data-stu-id="f1bb2-156">"-INF"</span></span>|<span data-ttu-id="f1bb2-157">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="f1bb2-157">Single.NegativeInfinity</span></span>|  
  
## <a name="string-to-double"></a><span data-ttu-id="f1bb2-158">Ciąg o podwójnej precyzji</span><span class="sxs-lookup"><span data-stu-id="f1bb2-158">String to Double</span></span>  
 <span data-ttu-id="f1bb2-159">W poniższej tabeli przedstawiono, jakiego typu jest generowane dla danego ciągów wejściowych podczas konwertowania ciągu na **pojedynczego** przy użyciu **todouble —** metody.</span><span class="sxs-lookup"><span data-stu-id="f1bb2-159">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToDouble** method.</span></span>  
  
|<span data-ttu-id="f1bb2-160">Parametr wejściowy prawidłowy ciąg</span><span class="sxs-lookup"><span data-stu-id="f1bb2-160">Valid string input parameter</span></span>|<span data-ttu-id="f1bb2-161">Typ danych wyjściowych .NET framework</span><span class="sxs-lookup"><span data-stu-id="f1bb2-161">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="f1bb2-162">"INF"</span><span class="sxs-lookup"><span data-stu-id="f1bb2-162">"INF"</span></span>|<span data-ttu-id="f1bb2-163">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="f1bb2-163">Double.PositiveInfinity</span></span>|  
|<span data-ttu-id="f1bb2-164">"-INF"</span><span class="sxs-lookup"><span data-stu-id="f1bb2-164">"-INF"</span></span>|<span data-ttu-id="f1bb2-165">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="f1bb2-165">Double.NegativeInfinity</span></span>|  
  
 <span data-ttu-id="f1bb2-166">Poniższy kod zapisy `<Infinity>INF</Infinity>`:</span><span class="sxs-lookup"><span data-stu-id="f1bb2-166">The following code writes `<Infinity>INF</Infinity>`:</span></span>  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1bb2-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1bb2-167">See Also</span></span>  
 [<span data-ttu-id="f1bb2-168">Konwersja typów danych XML</span><span class="sxs-lookup"><span data-stu-id="f1bb2-168">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [<span data-ttu-id="f1bb2-169">Konwertowanie typów programu .NET Framework na ciągi</span><span class="sxs-lookup"><span data-stu-id="f1bb2-169">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
