---
ms.openlocfilehash: a5b3e325c13d2f56532ebc6ebb5c259d565a4952
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235721"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a>Xmlschemaexception — teraz Ustawia pozycje wiersza prawidłowo

|   |   |
|---|---|
|Szczegóły|Jeśli <xref:System.Xml.Linq.LoadOptions.SetLineInfo> wartość jest przekazywana do metody obciążenia i wystąpi błąd sprawdzania poprawności, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> i <xref:System.Xml.Schema.XmlSchemaException.LinePosition> właściwości zawierają teraz informacje wiersza.|
|Sugestia|Kod obsługi wyjątków, który przyjmuje <xref:System.Xml.Schema.XmlSchemaException.LineNumber> i <xref:System.Xml.Schema.XmlSchemaException.LinePosition> nie będzie zaktualizować zestawu, ponieważ te właściwości można lokacji ustawi teraz poprawnie stosowania SetLineInfo podczas ładowania danych XML.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
