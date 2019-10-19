---
title: XmlReader. CreateSqlReader — Metoda (System. xml)
author: mairaw
ms.author: mairaw
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 302be4eff32d2c96a1571d291e0b289e77694db8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72584135"
---
# <a name="xmlreadercreatesqlreader-method"></a><span data-ttu-id="0164f-102">XmlReader. CreateSqlReader, Metoda</span><span class="sxs-lookup"><span data-stu-id="0164f-102">XmlReader.CreateSqlReader Method</span></span>

<span data-ttu-id="0164f-103">Tworzy nowe wystąpienie <xref:System.Xml.XmlReader> przy użyciu określonego strumienia, ustawień i informacji kontekstowych do analizy.</span><span class="sxs-lookup"><span data-stu-id="0164f-103">Creates a new <xref:System.Xml.XmlReader> instance using the specified stream, settings, and context information for parsing.</span></span>

```csharp
internal static XmlReader CreateSqlReader(Stream input, 
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a><span data-ttu-id="0164f-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="0164f-104">Parameters</span></span>

- <span data-ttu-id="0164f-105">`input`<xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="0164f-105">`input` <xref:System.IO.Stream></span></span>  
  <span data-ttu-id="0164f-106">Strumień zawierający dane XML.</span><span class="sxs-lookup"><span data-stu-id="0164f-106">The stream that contains the XML data.</span></span>

- <span data-ttu-id="0164f-107">`settings`<xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="0164f-107">`settings` <xref:System.Xml.XmlReaderSettings></span></span>  
  <span data-ttu-id="0164f-108">Ustawienia dla nowego wystąpienia <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="0164f-108">The settings for the new <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="0164f-109">Ta wartość może być `null`.</span><span class="sxs-lookup"><span data-stu-id="0164f-109">This value can be `null`.</span></span>

- <span data-ttu-id="0164f-110">`inputContext`<xref:System.Xml.XmlParserContext></span><span class="sxs-lookup"><span data-stu-id="0164f-110">`inputContext` <xref:System.Xml.XmlParserContext></span></span>  
  <span data-ttu-id="0164f-111">Informacje kontekstowe wymagane do przeanalizowania fragmentu kodu XML.</span><span class="sxs-lookup"><span data-stu-id="0164f-111">The context information required to parse the XML fragment.</span></span> <span data-ttu-id="0164f-112">Ta wartość może być `null`.</span><span class="sxs-lookup"><span data-stu-id="0164f-112">This value can be `null`.</span></span>

## <a name="returns"></a><span data-ttu-id="0164f-113">Zwraca</span><span class="sxs-lookup"><span data-stu-id="0164f-113">Returns</span></span>

<xref:System.Xml.XmlReader>  
<span data-ttu-id="0164f-114">Obiekt, który jest używany do odczytywania danych XML w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="0164f-114">An object that is used to read the XML data in the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="0164f-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0164f-115">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="0164f-116">Metoda `XmlReader.CreateSqlReader` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0164f-116">The `XmlReader.CreateSqlReader` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0164f-117">Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="0164f-117">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="0164f-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0164f-118">Requirements</span></span>

<span data-ttu-id="0164f-119">**Przestrzeń nazw:** <xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="0164f-119">**Namespace:** <xref:System.Xml></span></span>

<span data-ttu-id="0164f-120">**Zestaw:** System. XML. dll</span><span class="sxs-lookup"><span data-stu-id="0164f-120">**Assembly:** System.Xml.dll</span></span>

<span data-ttu-id="0164f-121">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="0164f-121">**.NET Framework versions:** Available since 2.0.</span></span>
