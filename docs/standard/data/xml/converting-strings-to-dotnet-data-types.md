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
ms.openlocfilehash: 376dd9df4666193f8e5a6be83f3fcaf5dc32f1a6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544604"
---
# <a name="converting-strings-to-net-framework-data-types"></a><span data-ttu-id="6565a-102">Konwertowanie ciągów na typy danych programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6565a-102">Converting Strings to .NET Framework Data Types</span></span>
<span data-ttu-id="6565a-103">Do przekonwertowania ciągu na typ danych .NET Framework, należy użyć **obiekt XmlConvert** metodę, która spełnia wymagania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6565a-103">If you want to convert a string to a .NET Framework data type, use the **XmlConvert** method that fits the application requirements.</span></span> <span data-ttu-id="6565a-104">Aby uzyskać listę wszystkich metod konwersji dostępnych w **obiekt XmlConvert** klasy, zobacz <xref:System.Xml.XmlConvert>.</span><span class="sxs-lookup"><span data-stu-id="6565a-104">For a list of all conversion methods available in the **XmlConvert** class, see <xref:System.Xml.XmlConvert>.</span></span>  
  
 <span data-ttu-id="6565a-105">Ciąg zwracany z **ToString** metodą jest wersję danych, które są przekazywane w ciągu.</span><span class="sxs-lookup"><span data-stu-id="6565a-105">The string returned from the **ToString** method is a string version of the data that is passed in.</span></span> <span data-ttu-id="6565a-106">Ponadto, istnieje kilka typów programu .NET Framework, które konwertują przy użyciu **obiekt XmlConvert** klasy, ale nie należy używać metod w **System.Convert** klasy.</span><span class="sxs-lookup"><span data-stu-id="6565a-106">Additionally, there are several .NET Framework types that convert using the **XmlConvert** class yet they do not use the methods in the **System.Convert** class.</span></span> <span data-ttu-id="6565a-107">**Obiekt XmlConvert** klasy następuje określenie typów danych schematu XML (XSD) i zawiera dane typu **obiekt XmlConvert** można mapować.</span><span class="sxs-lookup"><span data-stu-id="6565a-107">The **XmlConvert** class follows the XML Schema (XSD) data type specification and has a data type that the **XmlConvert** can map to.</span></span>  
  
 <span data-ttu-id="6565a-108">Poniższa tabela zawiera listę typów danych programu .NET Framework i typy parametrów, które są zwracane wartości przy użyciu mapowania typów danych schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="6565a-108">The following table lists .NET Framework data types and the string types that are returned using XML Schema (XSD) data type mapping.</span></span> <span data-ttu-id="6565a-109">Nie można przetworzyć tych typów programu .NET Framework za pomocą **System.Convert**.</span><span class="sxs-lookup"><span data-stu-id="6565a-109">These .NET Framework types cannot be processed using **System.Convert**.</span></span>  
  
|<span data-ttu-id="6565a-110">Typ programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6565a-110">.NET Framework type</span></span>|<span data-ttu-id="6565a-111">Ciąg zwracany</span><span class="sxs-lookup"><span data-stu-id="6565a-111">String returned</span></span>|  
|-------------------------|---------------------|  
|<span data-ttu-id="6565a-112">Boolean</span><span class="sxs-lookup"><span data-stu-id="6565a-112">Boolean</span></span>|<span data-ttu-id="6565a-113">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="6565a-113">"true", "false"</span></span>|  
|<span data-ttu-id="6565a-114">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="6565a-114">Single.PositiveInfinity</span></span>|<span data-ttu-id="6565a-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="6565a-115">"INF"</span></span>|  
|<span data-ttu-id="6565a-116">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="6565a-116">Single.NegativeInfinity</span></span>|<span data-ttu-id="6565a-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="6565a-117">"-INF"</span></span>|  
|<span data-ttu-id="6565a-118">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="6565a-118">Double.PositiveInfinity</span></span>|<span data-ttu-id="6565a-119">"INF"</span><span class="sxs-lookup"><span data-stu-id="6565a-119">"INF"</span></span>|  
|<span data-ttu-id="6565a-120">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="6565a-120">Double.NegativeInfinity</span></span>|<span data-ttu-id="6565a-121">"-INF"</span><span class="sxs-lookup"><span data-stu-id="6565a-121">"-INF"</span></span>|  
|<span data-ttu-id="6565a-122">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="6565a-122">DateTime</span></span>|<span data-ttu-id="6565a-123">Format to "RRRR-MM-ddTHH:mm:sszzzzzz" i jego podzbiory.</span><span class="sxs-lookup"><span data-stu-id="6565a-123">Format is "yyyy-MM-ddTHH:mm:sszzzzzz" and its subsets.</span></span>|  
|<span data-ttu-id="6565a-124">Przedział czasu</span><span class="sxs-lookup"><span data-stu-id="6565a-124">Timespan</span></span>|<span data-ttu-id="6565a-125">Format jest PnYnMnTnHnMnS czyli `P2Y10M15DT10H30M20S` to wartość typu duration 2 lat, 10 miesięcy, 15 dni, 10 godzin, 30 minut, a 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="6565a-125">Format is PnYnMnTnHnMnS that is, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10 hours, 30 minutes, and 20 seconds.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="6565a-126">Jeśli konwersja żadnego z typów programu .NET Framework wymienione w tabeli na ciąg za pośrednictwem **ToString** metody, w zwracanym ciągu nie jest typu podstawowego, ale typ ciągu schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="6565a-126">If converting any of the .NET Framework types listed in the table to a string using the **ToString** method, the returned string is not the base type, but the XML Schema (XSD) string type.</span></span>  
  
 <span data-ttu-id="6565a-127">**Daty/godziny** i **Timespan** typ wartości różni się w tym **daty/godziny** reprezentuje moment w czasie, natomiast **TimeSpan** reprezentuje przedział czasu.</span><span class="sxs-lookup"><span data-stu-id="6565a-127">The **DateTime** and **Timespan** value type differs in that a **DateTime** represents an instant in time, whereas a **TimeSpan** represents a time interval.</span></span> <span data-ttu-id="6565a-128">**Daty/godziny** i **Timespan** formaty są określone w specyfikacji typy danych schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="6565a-128">The **DateTime** and **Timespan** formats are specified in the XML Schema (XSD) data types specification.</span></span> <span data-ttu-id="6565a-129">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="6565a-129">For example:</span></span>  
  
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
  
 <span data-ttu-id="6565a-130">**Output**</span><span class="sxs-lookup"><span data-stu-id="6565a-130">**Output**</span></span>  
  
 <span data-ttu-id="6565a-131">`<Date>2001-08-04T00:00:00</Date>`.</span><span class="sxs-lookup"><span data-stu-id="6565a-131">`<Date>2001-08-04T00:00:00</Date>`.</span></span>  
  
 <span data-ttu-id="6565a-132">Poniższy kod konwertuje liczbę całkowitą na ciąg:</span><span class="sxs-lookup"><span data-stu-id="6565a-132">The following code converts an integer to a string:</span></span>  
  
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
  
 <span data-ttu-id="6565a-133">**Output**</span><span class="sxs-lookup"><span data-stu-id="6565a-133">**Output**</span></span>  
  
 `<Number>200</Number>`  
  
 <span data-ttu-id="6565a-134">Jednak Jeśli konwertujesz ciąg **logiczna**, **pojedynczego**, lub **Double**, typ .NET Framework, która jest zwracana nie jest taki sam jak typ zwracany, gdy za pomocą **System.Convert** klasy.</span><span class="sxs-lookup"><span data-stu-id="6565a-134">However, if you are converting a string to **Boolean**, **Single**, or **Double**, the .NET Framework type that is returned is not the same as the type returned when using the **System.Convert** class.</span></span>  
  
## <a name="string-to-boolean"></a><span data-ttu-id="6565a-135">Ciąg, aby atrybut typu wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="6565a-135">String to Boolean</span></span>  
 <span data-ttu-id="6565a-136">W poniższej tabeli przedstawiono, jaki typ jest generowany dla danego ciągi wejściowe podczas konwertowania ciągu do **logiczna** przy użyciu **ToBoolean** metody.</span><span class="sxs-lookup"><span data-stu-id="6565a-136">The following table shows what type is generated for the given input strings, when converting a string to **Boolean** using the **ToBoolean** method.</span></span>  
  
|<span data-ttu-id="6565a-137">Parametr wejściowy prawidłowy ciąg</span><span class="sxs-lookup"><span data-stu-id="6565a-137">Valid string input parameter</span></span>|<span data-ttu-id="6565a-138">Typ danych wyjściowych .NET framework</span><span class="sxs-lookup"><span data-stu-id="6565a-138">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="6565a-139">"true"</span><span class="sxs-lookup"><span data-stu-id="6565a-139">"true"</span></span>|<span data-ttu-id="6565a-140">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="6565a-140">Boolean.True</span></span>|  
|<span data-ttu-id="6565a-141">"1"</span><span class="sxs-lookup"><span data-stu-id="6565a-141">"1"</span></span>|<span data-ttu-id="6565a-142">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="6565a-142">Boolean.True</span></span>|  
|<span data-ttu-id="6565a-143">"false"</span><span class="sxs-lookup"><span data-stu-id="6565a-143">"false"</span></span>|<span data-ttu-id="6565a-144">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="6565a-144">Boolean.False</span></span>|  
|<span data-ttu-id="6565a-145">„0”</span><span class="sxs-lookup"><span data-stu-id="6565a-145">"0"</span></span>|<span data-ttu-id="6565a-146">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="6565a-146">Boolean.False</span></span>|  
  
 <span data-ttu-id="6565a-147">Na przykład biorąc pod uwagę następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="6565a-147">For example, given the following XML:</span></span>  
  
 <span data-ttu-id="6565a-148">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="6565a-148">**Input**</span></span>  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 <span data-ttu-id="6565a-149">Jednocześnie może być rozumiany przez następujący kod i **bDane wartości** jest **System.Boolean.True**:</span><span class="sxs-lookup"><span data-stu-id="6565a-149">Both can be understood by the following code, and **bvalue** is **System.Boolean.True**:</span></span>  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a><span data-ttu-id="6565a-150">Ciąg na wartość typu Single</span><span class="sxs-lookup"><span data-stu-id="6565a-150">String to Single</span></span>  
 <span data-ttu-id="6565a-151">W poniższej tabeli przedstawiono, jaki typ jest generowany dla danego ciągi wejściowe podczas konwertowania ciągu do **pojedynczego** przy użyciu **tosingle —** metody.</span><span class="sxs-lookup"><span data-stu-id="6565a-151">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToSingle** method.</span></span>  
  
|<span data-ttu-id="6565a-152">Parametr wejściowy prawidłowy ciąg</span><span class="sxs-lookup"><span data-stu-id="6565a-152">Valid string input parameter</span></span>|<span data-ttu-id="6565a-153">Typ danych wyjściowych .NET framework</span><span class="sxs-lookup"><span data-stu-id="6565a-153">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="6565a-154">"INF"</span><span class="sxs-lookup"><span data-stu-id="6565a-154">"INF"</span></span>|<span data-ttu-id="6565a-155">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="6565a-155">Single.PositiveInfinity</span></span>|  
|<span data-ttu-id="6565a-156">"-INF"</span><span class="sxs-lookup"><span data-stu-id="6565a-156">"-INF"</span></span>|<span data-ttu-id="6565a-157">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="6565a-157">Single.NegativeInfinity</span></span>|  
  
## <a name="string-to-double"></a><span data-ttu-id="6565a-158">Ciąg na wartość typu Double</span><span class="sxs-lookup"><span data-stu-id="6565a-158">String to Double</span></span>  
 <span data-ttu-id="6565a-159">W poniższej tabeli przedstawiono, jaki typ jest generowany dla danego ciągi wejściowe podczas konwertowania ciągu do **pojedynczego** przy użyciu **todouble —** metody.</span><span class="sxs-lookup"><span data-stu-id="6565a-159">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToDouble** method.</span></span>  
  
|<span data-ttu-id="6565a-160">Parametr wejściowy prawidłowy ciąg</span><span class="sxs-lookup"><span data-stu-id="6565a-160">Valid string input parameter</span></span>|<span data-ttu-id="6565a-161">Typ danych wyjściowych .NET framework</span><span class="sxs-lookup"><span data-stu-id="6565a-161">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="6565a-162">"INF"</span><span class="sxs-lookup"><span data-stu-id="6565a-162">"INF"</span></span>|<span data-ttu-id="6565a-163">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="6565a-163">Double.PositiveInfinity</span></span>|  
|<span data-ttu-id="6565a-164">"-INF"</span><span class="sxs-lookup"><span data-stu-id="6565a-164">"-INF"</span></span>|<span data-ttu-id="6565a-165">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="6565a-165">Double.NegativeInfinity</span></span>|  
  
 <span data-ttu-id="6565a-166">Poniższy kod zapisów `<Infinity>INF</Infinity>`:</span><span class="sxs-lookup"><span data-stu-id="6565a-166">The following code writes `<Infinity>INF</Infinity>`:</span></span>  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a><span data-ttu-id="6565a-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6565a-167">See also</span></span>

- [<span data-ttu-id="6565a-168">Konwersja typów danych XML</span><span class="sxs-lookup"><span data-stu-id="6565a-168">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [<span data-ttu-id="6565a-169">Konwertowanie typów programu .NET Framework na ciągi</span><span class="sxs-lookup"><span data-stu-id="6565a-169">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
