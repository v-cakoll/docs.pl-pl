---
ms.openlocfilehash: 68da7216890da1819a994161507355a0b5ea1f9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857508"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a>SignedXml i EncryptedXml Przełomowe zmiany

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.6.2 zabezpieczeń <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=name> <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=name> poprawki i prowadzić do różnych zachowań w czasie wykonywania. Na przykład:<ul><li>Jeśli dokument ma wiele elementów z tym samym <code>id</code> atrybutem i podpis jest przeznaczony dla jednego z tych elementów jako katalog główny podpisu, dokument zostanie teraz uznany za nieprawidłowy.</li><li>Dokumenty używające niekaonowych algorytmów przekształcania XPath w odwołaniach są teraz uważane za nieprawidłowe.</li><li>Dokumenty używające niekaonowych algorytmów przekształcania XSLT w odwołaniach są teraz uznawane za nieprawidłowe.</li><li>Żaden program korzystający z podpisów odłączonych od zasobów zewnętrznych nie będzie w stanie tego zrobić.</li></ul>|
|Sugestia|Deweloperzy mogą chcieć <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> przejrzeć użycie i <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, <xref:System.Security.Cryptography.Xml.Transform> a także typy pochodzące z ponieważ odbiornik dokumentów może nie być w stanie go przetworzyć.|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|
