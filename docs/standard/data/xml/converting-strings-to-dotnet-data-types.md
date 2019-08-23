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
ms.openlocfilehash: 31f277d11cba8191c326d56f017b8acc6503c6b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968712"
---
# <a name="converting-strings-to-net-framework-data-types"></a><span data-ttu-id="2dd0e-102">Konwertowanie ciągów na typy danych programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2dd0e-102">Converting Strings to .NET Framework Data Types</span></span>
<span data-ttu-id="2dd0e-103">Jeśli chcesz przekonwertować ciąg na typ danych .NET Framework, użyj metody XmlConvert, która pasuje do wymagań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2dd0e-103">If you want to convert a string to a .NET Framework data type, use the **XmlConvert** method that fits the application requirements.</span></span> <span data-ttu-id="2dd0e-104">Aby uzyskać listę wszystkich metod konwersji dostępnych w klasie XmlConvert, zobacz. <xref:System.Xml.XmlConvert></span><span class="sxs-lookup"><span data-stu-id="2dd0e-104">For a list of all conversion methods available in the **XmlConvert** class, see <xref:System.Xml.XmlConvert>.</span></span>  
  
 <span data-ttu-id="2dd0e-105">Ciąg zwracany przez metodę **ToString** jest ciągiem wersji, która została przekazana.</span><span class="sxs-lookup"><span data-stu-id="2dd0e-105">The string returned from the **ToString** method is a string version of the data that is passed in.</span></span> <span data-ttu-id="2dd0e-106">Ponadto istnieje kilka typów .NET Framework, które konwertują się przy użyciu klasy XmlConvert, ale nie używają metod w klasie **System. Convert** .</span><span class="sxs-lookup"><span data-stu-id="2dd0e-106">Additionally, there are several .NET Framework types that convert using the **XmlConvert** class yet they do not use the methods in the **System.Convert** class.</span></span> <span data-ttu-id="2dd0e-107">Klasa **XmlConvert** jest zgodna ze specyfikacją typu danych schematu XML (XSD) i ma typ danych, na który mapowanie XmlConvert może być mapowane.</span><span class="sxs-lookup"><span data-stu-id="2dd0e-107">The **XmlConvert** class follows the XML Schema (XSD) data type specification and has a data type that the **XmlConvert** can map to.</span></span>  
  
 <span data-ttu-id="2dd0e-108">Poniższa tabela zawiera listę typów danych .NET Framework i typy ciągów, które są zwracane przy użyciu mapowania typu danych schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="2dd0e-108">The following table lists .NET Framework data types and the string types that are returned using XML Schema (XSD) data type mapping.</span></span> <span data-ttu-id="2dd0e-109">Te typy .NET Framework nie mogą być przetwarzane przy użyciu funkcji **System. Convert**.</span><span class="sxs-lookup"><span data-stu-id="2dd0e-109">These .NET Framework types cannot be processed using **System.Convert**.</span></span>  
  
|<span data-ttu-id="2dd0e-110">Typ programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2dd0e-110">.NET Framework type</span></span>|<span data-ttu-id="2dd0e-111">Zwrócony ciąg</span><span class="sxs-lookup"><span data-stu-id="2dd0e-111">String returned</span></span>|  
|-------------------------|---------------------|  
|<span data-ttu-id="2dd0e-112">Boolean</span><span class="sxs-lookup"><span data-stu-id="2dd0e-112">Boolean</span></span>|<span data-ttu-id="2dd0e-113">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="2dd0e-113">"true", "false"</span></span>|  
|<span data-ttu-id="2dd0e-114">Single. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="2dd0e-114">Single.PositiveInfinity</span></span>|<span data-ttu-id="2dd0e-115">INF</span><span class="sxs-lookup"><span data-stu-id="2dd0e-115">"INF"</span></span>|  
|<span data-ttu-id="2dd0e-116">Single. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="2dd0e-116">Single.NegativeInfinity</span></span>|<span data-ttu-id="2dd0e-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="2dd0e-117">"-INF"</span></span>|  
|<span data-ttu-id="2dd0e-118">Double. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="2dd0e-118">Double.PositiveInfinity</span></span>|<span data-ttu-id="2dd0e-119">INF</span><span class="sxs-lookup"><span data-stu-id="2dd0e-119">"INF"</span></span>|  
|<span data-ttu-id="2dd0e-120">Double. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="2dd0e-120">Double.NegativeInfinity</span></span>|<span data-ttu-id="2dd0e-121">"-INF"</span><span class="sxs-lookup"><span data-stu-id="2dd0e-121">"-INF"</span></span>|  
|<span data-ttu-id="2dd0e-122">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2dd0e-122">DateTime</span></span>|<span data-ttu-id="2dd0e-123">Format to "RRRR-MM-DDTgg: mm: sszzzzzz" i jego podzestawy.</span><span class="sxs-lookup"><span data-stu-id="2dd0e-123">Format is "yyyy-MM-ddTHH:mm:sszzzzzz" and its subsets.</span></span>|  
|<span data-ttu-id="2dd0e-124">Timespan</span><span class="sxs-lookup"><span data-stu-id="2dd0e-124">Timespan</span></span>|<span data-ttu-id="2dd0e-125">Format to PnYnMnTnHnMnS, `P2Y10M15DT10H30M20S` czyli okres 2 lat, 10 miesięcy, 15 dni, 10 godzin, 30 minut i 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="2dd0e-125">Format is PnYnMnTnHnMnS that is, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10 hours, 30 minutes, and 20 seconds.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="2dd0e-126">W przypadku konwertowania dowolnego typu .NET Framework wymienionego w tabeli na ciąg przy użyciu metody **ToString** zwracany ciąg nie jest typem podstawowym, ale typ ciągu schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="2dd0e-126">If converting any of the .NET Framework types listed in the table to a string using the **ToString** method, the returned string is not the base type, but the XML Schema (XSD) string type.</span></span>  
  
 <span data-ttu-id="2dd0e-127">Typ wartości **DateTime** i **TimeSpan** różni się w tym, że element **DateTime** reprezentuje chwilę w czasie, podczas gdy obiekt **TimeSpan** reprezentuje przedział czasu.</span><span class="sxs-lookup"><span data-stu-id="2dd0e-127">The **DateTime** and **Timespan** value type differs in that a **DateTime** represents an instant in time, whereas a **TimeSpan** represents a time interval.</span></span> <span data-ttu-id="2dd0e-128">Formaty **DateTime** i **TimeSpan** są określone w specyfikacji typów danych schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="2dd0e-128">The **DateTime** and **Timespan** formats are specified in the XML Schema (XSD) data types specification.</span></span> <span data-ttu-id="2dd0e-129">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2dd0e-129">For example:</span></span>  
  
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
  
 <span data-ttu-id="2dd0e-130">**Output**</span><span class="sxs-lookup"><span data-stu-id="2dd0e-130">**Output**</span></span>  
  
 <span data-ttu-id="2dd0e-131">`<Date>2001-08-04T00:00:00</Date>`.</span><span class="sxs-lookup"><span data-stu-id="2dd0e-131">`<Date>2001-08-04T00:00:00</Date>`.</span></span>  
  
 <span data-ttu-id="2dd0e-132">Poniższy kod konwertuje liczbę całkowitą na ciąg:</span><span class="sxs-lookup"><span data-stu-id="2dd0e-132">The following code converts an integer to a string:</span></span>  
  
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
  
 <span data-ttu-id="2dd0e-133">**Output**</span><span class="sxs-lookup"><span data-stu-id="2dd0e-133">**Output**</span></span>  
  
 `<Number>200</Number>`  
  
 <span data-ttu-id="2dd0e-134">Jeśli jednak konwertujesz ciąg na **wartość Boolean**, **Single**lub **Double**, zwracany typ .NET Framework nie jest taki sam jak typ zwracany podczas używania klasy **System. Convert** .</span><span class="sxs-lookup"><span data-stu-id="2dd0e-134">However, if you are converting a string to **Boolean**, **Single**, or **Double**, the .NET Framework type that is returned is not the same as the type returned when using the **System.Convert** class.</span></span>  
  
## <a name="string-to-boolean"></a><span data-ttu-id="2dd0e-135">Ciąg do wartości logicznej</span><span class="sxs-lookup"><span data-stu-id="2dd0e-135">String to Boolean</span></span>  
 <span data-ttu-id="2dd0e-136">W poniższej tabeli przedstawiono typ, który jest generowany dla danego ciągu wejściowego podczas konwertowania ciągu na **wartość logiczną** przy użyciu metody **ToBoolean** .</span><span class="sxs-lookup"><span data-stu-id="2dd0e-136">The following table shows what type is generated for the given input strings, when converting a string to **Boolean** using the **ToBoolean** method.</span></span>  
  
|<span data-ttu-id="2dd0e-137">Prawidłowy parametr wejściowy ciągu</span><span class="sxs-lookup"><span data-stu-id="2dd0e-137">Valid string input parameter</span></span>|<span data-ttu-id="2dd0e-138">Typ danych wyjściowych .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2dd0e-138">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="2dd0e-139">"true"</span><span class="sxs-lookup"><span data-stu-id="2dd0e-139">"true"</span></span>|<span data-ttu-id="2dd0e-140">Wartość logiczna. true</span><span class="sxs-lookup"><span data-stu-id="2dd0e-140">Boolean.True</span></span>|  
|<span data-ttu-id="2dd0e-141">"1"</span><span class="sxs-lookup"><span data-stu-id="2dd0e-141">"1"</span></span>|<span data-ttu-id="2dd0e-142">Wartość logiczna. true</span><span class="sxs-lookup"><span data-stu-id="2dd0e-142">Boolean.True</span></span>|  
|<span data-ttu-id="2dd0e-143">false</span><span class="sxs-lookup"><span data-stu-id="2dd0e-143">"false"</span></span>|<span data-ttu-id="2dd0e-144">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="2dd0e-144">Boolean.False</span></span>|  
|<span data-ttu-id="2dd0e-145">„0”</span><span class="sxs-lookup"><span data-stu-id="2dd0e-145">"0"</span></span>|<span data-ttu-id="2dd0e-146">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="2dd0e-146">Boolean.False</span></span>|  
  
 <span data-ttu-id="2dd0e-147">Na przykład, uwzględniając następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="2dd0e-147">For example, given the following XML:</span></span>  
  
 <span data-ttu-id="2dd0e-148">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="2dd0e-148">**Input**</span></span>  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 <span data-ttu-id="2dd0e-149">Obie te wartości można zrozumieć przy użyciu poniższego kodu, a **bValue** to **System. Boolean. true**:</span><span class="sxs-lookup"><span data-stu-id="2dd0e-149">Both can be understood by the following code, and **bvalue** is **System.Boolean.True**:</span></span>  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a><span data-ttu-id="2dd0e-150">Ciąg do jednego</span><span class="sxs-lookup"><span data-stu-id="2dd0e-150">String to Single</span></span>  
 <span data-ttu-id="2dd0e-151">W poniższej tabeli przedstawiono typ, który jest generowany dla danych wejściowych ciągów, podczas konwertowania ciągu na **pojedynczy** przy użyciu metody **ToSingle —** .</span><span class="sxs-lookup"><span data-stu-id="2dd0e-151">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToSingle** method.</span></span>  
  
|<span data-ttu-id="2dd0e-152">Prawidłowy parametr wejściowy ciągu</span><span class="sxs-lookup"><span data-stu-id="2dd0e-152">Valid string input parameter</span></span>|<span data-ttu-id="2dd0e-153">Typ danych wyjściowych .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2dd0e-153">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="2dd0e-154">INF</span><span class="sxs-lookup"><span data-stu-id="2dd0e-154">"INF"</span></span>|<span data-ttu-id="2dd0e-155">Single. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="2dd0e-155">Single.PositiveInfinity</span></span>|  
|<span data-ttu-id="2dd0e-156">"-INF"</span><span class="sxs-lookup"><span data-stu-id="2dd0e-156">"-INF"</span></span>|<span data-ttu-id="2dd0e-157">Single. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="2dd0e-157">Single.NegativeInfinity</span></span>|  
  
## <a name="string-to-double"></a><span data-ttu-id="2dd0e-158">Ciąg na Double</span><span class="sxs-lookup"><span data-stu-id="2dd0e-158">String to Double</span></span>  
 <span data-ttu-id="2dd0e-159">W poniższej tabeli przedstawiono typ, który jest generowany dla danych wejściowych ciągów, podczas konwertowania ciągu na **pojedynczy** przy użyciu metody **ToDouble —** .</span><span class="sxs-lookup"><span data-stu-id="2dd0e-159">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToDouble** method.</span></span>  
  
|<span data-ttu-id="2dd0e-160">Prawidłowy parametr wejściowy ciągu</span><span class="sxs-lookup"><span data-stu-id="2dd0e-160">Valid string input parameter</span></span>|<span data-ttu-id="2dd0e-161">Typ danych wyjściowych .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2dd0e-161">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="2dd0e-162">INF</span><span class="sxs-lookup"><span data-stu-id="2dd0e-162">"INF"</span></span>|<span data-ttu-id="2dd0e-163">Double. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="2dd0e-163">Double.PositiveInfinity</span></span>|  
|<span data-ttu-id="2dd0e-164">"-INF"</span><span class="sxs-lookup"><span data-stu-id="2dd0e-164">"-INF"</span></span>|<span data-ttu-id="2dd0e-165">Double. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="2dd0e-165">Double.NegativeInfinity</span></span>|  
  
 <span data-ttu-id="2dd0e-166">Poniższy kod zapisuje `<Infinity>INF</Infinity>`:</span><span class="sxs-lookup"><span data-stu-id="2dd0e-166">The following code writes `<Infinity>INF</Infinity>`:</span></span>  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a><span data-ttu-id="2dd0e-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2dd0e-167">See also</span></span>

- [<span data-ttu-id="2dd0e-168">Konwersja typów danych XML</span><span class="sxs-lookup"><span data-stu-id="2dd0e-168">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [<span data-ttu-id="2dd0e-169">Konwertowanie typów programu .NET Framework na ciągi</span><span class="sxs-lookup"><span data-stu-id="2dd0e-169">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
