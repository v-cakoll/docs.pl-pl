---
ms.openlocfilehash: 8cc4f2ba2923774ef4e4e6861a89a7797ca988e1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621202"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a>Zmiany SignedXml i EncryptedXml

#### <a name="details"></a>Szczegóły

W .NET Framework 4.6.2, poprawki zabezpieczeń w <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> i <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> prowadzą do różnych zachowań w czasie wykonywania. Na przykład<ul><li>Jeśli dokument ma wiele elementów z tym samym <code>id</code> atrybutem, a podpis jednego z tych elementów jako element główny podpisu, dokument będzie teraz traktowany jako nieprawidłowy.</li><li>Dokumenty używające niekanonicznych algorytmów transformacji XPath w odwołaniach są teraz uznawane za nieprawidłowe.</li><li>Dokumenty korzystające z algorytmów transformacji XSLT inne niż kanoniczne w odwołaniach są teraz traktowane jako nieprawidłowe.</li><li>Nie będzie można wykonać żadnego programu korzystającego z odłączonych podpisów zasobów zewnętrznych.</li></ul>

#### <a name="suggestion"></a>Sugestia

Deweloperzy mogą chcieć przejrzeć użycie <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> i <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> , jak również typy pochodne od momentu, gdy <xref:System.Security.Cryptography.Xml.Transform> odbiorca dokumentu może nie być w stanie go przetworzyć.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|
