---
title: "XML uwagi dotyczące implementacji pomocy technicznej dla typu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8c2706782ed1242ecdb5af1fdfab7a3f24e19236
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="xml-type-support-implementation-notes"></a><span data-ttu-id="d4685-102">XML uwagi dotyczące implementacji pomocy technicznej dla typu</span><span class="sxs-lookup"><span data-stu-id="d4685-102">XML Type Support Implementation Notes</span></span>
<span data-ttu-id="d4685-103">W tym temacie opisano niektóre szczegóły implementacji, które mają być znane.</span><span class="sxs-lookup"><span data-stu-id="d4685-103">This topic describes some implementation details that you want to be aware of.</span></span>  
  
## <a name="list-mappings"></a><span data-ttu-id="d4685-104">Lista mapowań</span><span class="sxs-lookup"><span data-stu-id="d4685-104">List Mappings</span></span>  
 <span data-ttu-id="d4685-105"><xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type []**, i <xref:System.String> typy są używane do reprezentowania schematu XML definition language (XSD) listy typów.</span><span class="sxs-lookup"><span data-stu-id="d4685-105">The <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type[]**, and <xref:System.String> types are used to represent XML Schema definition language (XSD) list types.</span></span>  
  
## <a name="union-mappings"></a><span data-ttu-id="d4685-106">Mapowania Unii</span><span class="sxs-lookup"><span data-stu-id="d4685-106">Union Mappings</span></span>  
 <span data-ttu-id="d4685-107">Typy Unii są reprezentowane <xref:System.Xml.Schema.XmlAtomicValue> lub <xref:System.String> typu.</span><span class="sxs-lookup"><span data-stu-id="d4685-107">Union types are represented using the <xref:System.Xml.Schema.XmlAtomicValue> or <xref:System.String> type.</span></span> <span data-ttu-id="d4685-108">Typ źródłowy lub docelowy typ muszą więc być zawsze albo <xref:System.String> lub <xref:System.Xml.Schema.XmlAtomicValue>.</span><span class="sxs-lookup"><span data-stu-id="d4685-108">The source type or the destination type must therefore always be either <xref:System.String> or <xref:System.Xml.Schema.XmlAtomicValue>.</span></span>  
  
 <span data-ttu-id="d4685-109">Jeśli <xref:System.Xml.Schema.XmlSchemaDatatype> obiekt reprezentuje typ listy Konwertuje obiekt do listy co najmniej jeden obiekt wartości ciągu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="d4685-109">If the <xref:System.Xml.Schema.XmlSchemaDatatype> object represents a list type the object converts the input string value to a list of one or more objects.</span></span> <span data-ttu-id="d4685-110">Jeśli <xref:System.Xml.Schema.XmlSchemaDatatype> reprezentuje typ Unii, a następnie podejmowana jest próba można przeanalizować wartości wejściowej jako typ elementu Członkowskiego Unii.</span><span class="sxs-lookup"><span data-stu-id="d4685-110">If the <xref:System.Xml.Schema.XmlSchemaDatatype> represents a union type then an attempt is made to parse the input value as a member type of the union.</span></span> <span data-ttu-id="d4685-111">Jeśli próba analizy nie powiedzie się następnie konwersji jest usiłowano następny element członkowski Unii i tak dalej do momentu konwersji zakończy się pomyślnie lub nie ma żadnych typów elementu członkowskiego próby, w którym to przypadku jest zwracany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d4685-111">If the parse attempt fails then the conversion is attempted with the next member of the union and so on until the conversion is successful, or there are no other member types to try, in which case an exception is thrown.</span></span>  
  
## <a name="differences-between-clr-and-xml-data-types"></a><span data-ttu-id="d4685-112">Różnice między CLR i typów danych XML</span><span class="sxs-lookup"><span data-stu-id="d4685-112">Differences Between CLR and XML Data Types</span></span>  
 <span data-ttu-id="d4685-113">Poniżej przedstawiono niektóre niezgodności, które mogą wystąpić między typami CLR i typów danych XML i sposób obsługi.</span><span class="sxs-lookup"><span data-stu-id="d4685-113">The following describes certain mismatches that can occur between CLR types and XML data types and how they are handled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4685-114">`xs` Prefiks jest mapowany na http://www.w3.org/2001/XMLSchema i identyfikator URI przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d4685-114">The `xs` prefix is mapped to the http://www.w3.org/2001/XMLSchema and namespace URI.</span></span>  
  
### <a name="systemtimespan-and-xsduration"></a><span data-ttu-id="d4685-115">Obiekt System.TimeSpan i DURATION</span><span class="sxs-lookup"><span data-stu-id="d4685-115">System.TimeSpan and xs:duration</span></span>  
 <span data-ttu-id="d4685-116">`xs:duration` Typu częściowo porządkowania, w tym brak niektórych wartości czasu trwania, które różnią się jednak równoważne.</span><span class="sxs-lookup"><span data-stu-id="d4685-116">The `xs:duration` type is partially ordered in that there are certain duration values that are different but equivalent.</span></span> <span data-ttu-id="d4685-117">Oznacza to, że dla `xs:duration` typu wartości, takich jak 1 miesiąc (P1M) jest mniejsza niż 32 dni (P32D), przekracza 27 dni (P27D) i jest odpowiednikiem 28, 29 lub 30 dni.</span><span class="sxs-lookup"><span data-stu-id="d4685-117">This means that for the `xs:duration` type value such as 1 month (P1M) is less than 32 days (P32D), larger than 27 days (P27D) and equivalent to 28, 29 or 30 days.</span></span>  
  
 <span data-ttu-id="d4685-118"><xref:System.TimeSpan> Klasa nie obsługuje częściowe porządkowanie.</span><span class="sxs-lookup"><span data-stu-id="d4685-118">The <xref:System.TimeSpan> class does not support this partial ordering.</span></span> <span data-ttu-id="d4685-119">Zamiast tego należy go wybiera określoną liczbę dni do 1 roku i 1 miesiąc; 365 dni i 30 dni odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="d4685-119">Instead, it picks a specific number of days for 1 year and 1 month; 365 days and 30 days respectively.</span></span>  
  
 <span data-ttu-id="d4685-120">Aby uzyskać więcej informacji na temat `xs:duration` typu, zobacz W3C XML schematu część 2: zalecenie typów danych w http://www.w3.org/TR/xmlschema-2/.</span><span class="sxs-lookup"><span data-stu-id="d4685-120">For more information on the `xs:duration` type, see the W3C XML Schema Part 2: Datatypes Recommendation at http://www.w3.org/TR/xmlschema-2/.</span></span>  
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a><span data-ttu-id="d4685-121">xs: Time, typy data gregoriańska i System.DateTime</span><span class="sxs-lookup"><span data-stu-id="d4685-121">xs:time, Gregorian Date Types, and System.DateTime</span></span>  
 <span data-ttu-id="d4685-122">Gdy `xs:time` wartość jest mapowany na <xref:System.DateTime> obiektu, <xref:System.DateTime.MinValue> pole służy do inicjowania właściwości daty <xref:System.DateTime> obiektu (takich jak <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, i <xref:System.DateTime.Day%2A>) do najmniejszego możliwego <xref:System.DateTime> wartość.</span><span class="sxs-lookup"><span data-stu-id="d4685-122">When an `xs:time` value is mapped to a <xref:System.DateTime> object, the <xref:System.DateTime.MinValue> field is used to initialize the date properties of the <xref:System.DateTime> object (such as <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, and <xref:System.DateTime.Day%2A>) to the smallest possible <xref:System.DateTime> value.</span></span>  
  
 <span data-ttu-id="d4685-123">Podobnie wystąpienia `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` i `xs:gMonthDay` również są mapowane na <xref:System.DateTime> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d4685-123">Similarly, instances of `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` and `xs:gMonthDay` are also mapped to a <xref:System.DateTime> object.</span></span> <span data-ttu-id="d4685-124">Nieużywane właściwości <xref:System.DateTime> zainicjowany z obiektu <xref:System.DateTime.MinValue>.</span><span class="sxs-lookup"><span data-stu-id="d4685-124">Unused properties on the <xref:System.DateTime> object are initialized to those from <xref:System.DateTime.MinValue>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4685-125">Nie należy polegać na <xref:System.DateTime.Year%2A?displayProperty=nameWithType> wartość, gdy zawartość jest typu `xs:gMonthDay`.</span><span class="sxs-lookup"><span data-stu-id="d4685-125">You cannot rely on the <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value when the content is typed as `xs:gMonthDay`.</span></span> <span data-ttu-id="d4685-126"><xref:System.DateTime.Year%2A?displayProperty=nameWithType> Ma zawsze wartość 1904 w takim przypadku.</span><span class="sxs-lookup"><span data-stu-id="d4685-126">The <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value is always set to 1904 in this case.</span></span>  
  
### <a name="xsanyuri-and-systemuri"></a><span data-ttu-id="d4685-127">xs:anyURI i System.Uri</span><span class="sxs-lookup"><span data-stu-id="d4685-127">xs:anyURI and System.Uri</span></span>  
 <span data-ttu-id="d4685-128">Gdy wystąpienie klasy `xs:anyURI` że reprezentuje względny identyfikator URI, jest mapowany na <xref:System.Uri>, <xref:System.Uri> obiekt nie ma podstawowego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="d4685-128">When an instance of `xs:anyURI` that represents a relative URI is mapped to a <xref:System.Uri>, the <xref:System.Uri> object does not have a base URI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4685-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4685-129">See Also</span></span>  
 [<span data-ttu-id="d4685-130">Obsługa typu w ramach klas zestawu System.Xml</span><span class="sxs-lookup"><span data-stu-id="d4685-130">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
