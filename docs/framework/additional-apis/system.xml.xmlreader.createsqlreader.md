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
# <a name="xmlreadercreatesqlreader-method"></a>XmlReader. CreateSqlReader, Metoda

Tworzy nowe wystąpienie <xref:System.Xml.XmlReader> przy użyciu określonego strumienia, ustawień i informacji kontekstowych do analizy.

```csharp
internal static XmlReader CreateSqlReader(Stream input, 
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a>Parametry

- `input`<xref:System.IO.Stream>  
  Strumień zawierający dane XML.

- `settings`<xref:System.Xml.XmlReaderSettings>  
  Ustawienia dla nowego wystąpienia <xref:System.Xml.XmlReader>. Ta wartość może być `null`.

- `inputContext`<xref:System.Xml.XmlParserContext>  
  Informacje kontekstowe wymagane do przeanalizowania fragmentu kodu XML. Ta wartość może być `null`.

## <a name="returns"></a>Zwraca

<xref:System.Xml.XmlReader>  
Obiekt, który jest używany do odczytywania danych XML w strumieniu.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Metoda `XmlReader.CreateSqlReader` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:** <xref:System.Xml>

**Zestaw:** System. XML. dll

**.NET Framework wersje:** Dostępne od 2,0.
