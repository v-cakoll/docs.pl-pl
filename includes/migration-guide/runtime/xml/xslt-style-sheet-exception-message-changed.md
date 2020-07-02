---
ms.openlocfilehash: 5c27e8acdf30533036546ba4cca9e06877bde362
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620525"
---
### <a name="xslt-style-sheet-exception-message-changed"></a>Zmieniono komunikat o wyjątku arkusza stylów XSLT

#### <a name="details"></a>Szczegóły

W .NET Framework 4,5 tekst komunikatu o błędzie, gdy plik XSLT jest zbyt złożony, to &quot; arkusz stylów jest zbyt złożony. &quot; W poprzednich wersjach komunikat o błędzie był &quot; błędem kompilacji XSLT. &quot; Kod aplikacji, który zależy od tekstu komunikatu o błędzie, przestanie działać. Jednak typy wyjątków pozostają takie same, więc zmiana ta nie powinna mieć rzeczywistego wpływu.

#### <a name="suggestion"></a>Sugestia

Zaktualizuj dowolny kod aplikacji w zależności od komunikatu o wyjątku z tego warunku błędu, aby oczekiwać nowej wiadomości lub (nawet lepiej) zaktualizować kod, tak aby był zależny tylko od typu wyjątku ( <xref:System.Xml.Xsl.XsltException?displayProperty=fullName> ), który nie został zmieniony.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li></ul>|
