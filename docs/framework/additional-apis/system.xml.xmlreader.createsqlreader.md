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
# <a name="xmlreadercreatesqlreader-method"></a>XmlReader.CreateSqlReader, metoda

Tworzy nowe <xref:System.Xml.XmlReader> wystąpienie przy użyciu określonego strumienia, ustawienia i informacje kontekstowe do analizowania.

```csharp
internal static XmlReader CreateSqlReader(Stream input,
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a>Parametry

- `input` <xref:System.IO.Stream>  
  Strumień, który zawiera dane XML.

- `settings` <xref:System.Xml.XmlReaderSettings>  
  Ustawienia nowego <xref:System.Xml.XmlReader> wystąpienia. Ta wartość `null`może być .

- `inputContext` <xref:System.Xml.XmlParserContext>  
  Informacje kontekstu wymagane do przeanalizowania fragmentu XML. Ta wartość `null`może być .

## <a name="returns"></a>Zwraca

<xref:System.Xml.XmlReader>  
Obiekt, który jest używany do odczytu danych XML w strumieniu.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Metoda `XmlReader.CreateSqlReader` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje tej metody w aplikacji produkcyjnej w żadnych okolicznościach.

## <a name="requirements"></a>Wymagania

**Obszar nazw:**<xref:System.Xml>

**Montaż:** System.xml.dll

**Wersje programu .NET Framework:** Dostępne od 2.0.
