---
ms.openlocfilehash: a5b3e325c13d2f56532ebc6ebb5c259d565a4952
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379623"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a>Xmlschemaexception — teraz Ustawia pozycje wiersza prawidłowo

|   |   |
|---|---|
|Szczegóły|Jeśli <xref:System.Xml.Linq.LoadOptions.SetLineInfo> wartość jest przekazywana do metody obciążenia i wystąpi błąd sprawdzania poprawności, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> i <xref:System.Xml.Schema.XmlSchemaException.LinePosition> właściwości zawierają teraz informacje wiersza.|
|Sugestia|Kod obsługi wyjątków, który przyjmuje <xref:System.Xml.Schema.XmlSchemaException.LineNumber> i <xref:System.Xml.Schema.XmlSchemaException.LinePosition> nie będzie zaktualizować zestawu, ponieważ te właściwości można lokacji ustawi teraz poprawnie stosowania SetLineInfo podczas ładowania danych XML.|
|Scope|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
