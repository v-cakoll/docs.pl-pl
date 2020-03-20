---
title: XmlReader.CreateSqlReader Metoda (System.Xml)
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 7bd2ef5158516acede47f73f9937d06159bc16c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155742"
---
# <a name="xmlreadercreatesqlreader-method"></a><span data-ttu-id="397e8-102">XmlReader.CreateSqlReader, metoda</span><span class="sxs-lookup"><span data-stu-id="397e8-102">XmlReader.CreateSqlReader Method</span></span>

<span data-ttu-id="397e8-103">Tworzy nowe <xref:System.Xml.XmlReader> wystąpienie przy użyciu określonego strumienia, ustawienia i informacje kontekstowe do analizowania.</span><span class="sxs-lookup"><span data-stu-id="397e8-103">Creates a new <xref:System.Xml.XmlReader> instance using the specified stream, settings, and context information for parsing.</span></span>

```csharp
internal static XmlReader CreateSqlReader(Stream input,
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a><span data-ttu-id="397e8-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="397e8-104">Parameters</span></span>

- <span data-ttu-id="397e8-105">`input` <xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="397e8-105">`input` <xref:System.IO.Stream></span></span>  
  <span data-ttu-id="397e8-106">Strumień, który zawiera dane XML.</span><span class="sxs-lookup"><span data-stu-id="397e8-106">The stream that contains the XML data.</span></span>

- <span data-ttu-id="397e8-107">`settings` <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="397e8-107">`settings` <xref:System.Xml.XmlReaderSettings></span></span>  
  <span data-ttu-id="397e8-108">Ustawienia nowego <xref:System.Xml.XmlReader> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="397e8-108">The settings for the new <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="397e8-109">Ta wartość `null`może być .</span><span class="sxs-lookup"><span data-stu-id="397e8-109">This value can be `null`.</span></span>

- <span data-ttu-id="397e8-110">`inputContext` <xref:System.Xml.XmlParserContext></span><span class="sxs-lookup"><span data-stu-id="397e8-110">`inputContext` <xref:System.Xml.XmlParserContext></span></span>  
  <span data-ttu-id="397e8-111">Informacje kontekstu wymagane do przeanalizowania fragmentu XML.</span><span class="sxs-lookup"><span data-stu-id="397e8-111">The context information required to parse the XML fragment.</span></span> <span data-ttu-id="397e8-112">Ta wartość `null`może być .</span><span class="sxs-lookup"><span data-stu-id="397e8-112">This value can be `null`.</span></span>

## <a name="returns"></a><span data-ttu-id="397e8-113">Zwraca</span><span class="sxs-lookup"><span data-stu-id="397e8-113">Returns</span></span>

<xref:System.Xml.XmlReader>  
<span data-ttu-id="397e8-114">Obiekt, który jest używany do odczytu danych XML w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="397e8-114">An object that is used to read the XML data in the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="397e8-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="397e8-115">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="397e8-116">Metoda `XmlReader.CreateSqlReader` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="397e8-116">The `XmlReader.CreateSqlReader` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="397e8-117">Firma Microsoft nie obsługuje tej metody w aplikacji produkcyjnej w żadnych okolicznościach.</span><span class="sxs-lookup"><span data-stu-id="397e8-117">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="397e8-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="397e8-118">Requirements</span></span>

<span data-ttu-id="397e8-119">**Obszar nazw:**<xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="397e8-119">**Namespace:** <xref:System.Xml></span></span>

<span data-ttu-id="397e8-120">**Montaż:** System.xml.dll</span><span class="sxs-lookup"><span data-stu-id="397e8-120">**Assembly:** System.Xml.dll</span></span>

<span data-ttu-id="397e8-121">**Wersje programu .NET Framework:** Dostępne od 2.0.</span><span class="sxs-lookup"><span data-stu-id="397e8-121">**.NET Framework versions:** Available since 2.0.</span></span>
