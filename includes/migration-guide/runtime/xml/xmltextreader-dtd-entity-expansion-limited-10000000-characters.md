---
ms.openlocfilehash: fdec6671cbf2dae0d72dfaec07f162058b38cf9d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620513"
---
### <a name="xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a>Rozwinięcie jednostki DTD XmlTextReader jest ograniczone do 10 000 000 znaków

#### <a name="details"></a>Szczegóły

Rozwinięcie jednostki DTD jest teraz ograniczone do 10 000 000 znaków. Możliwość ładowania plików XML bez rozszerzenia jednostki DTD lub z możliwością ograniczonego rozszerzania jednostki DTD pozostaje bez zmian. Nie można ładować plików z jednostkami DTD, które są rozszerzane do ponad 10 000 000 znaków. Zostanie zgłoszony wyjątek.

#### <a name="suggestion"></a>Sugestia

Jeśli limit rozwinięcia jednostki DTD jest zbyt niski 10 000 000, wartość można zastąpić <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities> właściwością. <xref:System.Xml.XmlReaderSettings?displayProperty=fullName>Z prawidłową <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName> wartością można przesłać do elementu <code>XmlReader.Create</code> , który ma <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> (IE). <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Xml.XmlTextReader?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.Xml.XmlNameTable)></li></ul>|
