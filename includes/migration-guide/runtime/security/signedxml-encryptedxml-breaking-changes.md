---
ms.openlocfilehash: 68da7216890da1819a994161507355a0b5ea1f9f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804706"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a>SignedXml i EncryptedXml fundamentalne zmiany

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6.2, poprawek zabezpieczeń <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=name> i <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=name> prowadzić do różnych zachowań w czasie wykonywania. Na przykład<ul><li>Jeśli dokument ma wiele elementów o takiej samej <code>id</code> atrybut i podpisu jest przeznaczony dla jednego z tych elementów jako użytkownik główny podpisu, dokumentu będą teraz uznawane za nieprawidłowe.</li><li>Dokumenty przy użyciu-canonical algorytmy przekształcenie XPath w odwołaniach teraz są uznawane za nieprawidłowe.</li><li>Dokumenty przy użyciu-canonical algorytmy transformacji XSLT w odwołaniach są teraz należy wziąć pod uwagę nieprawidłowy.</li><li>Wszelkie program korzystające z zewnętrznego zasobu odłączyć podpisów można to zrobić.</li></ul>|
|Sugestia|Deweloperzy mogą chcą Sprawdź sposób użycia <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> i <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, jak również typy pochodne <xref:System.Security.Cryptography.Xml.Transform> od odbiorcy dokumentu nie można go przetworzyć.|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|
