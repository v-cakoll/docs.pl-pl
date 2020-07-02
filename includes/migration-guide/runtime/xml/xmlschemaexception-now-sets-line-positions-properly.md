---
ms.openlocfilehash: c3e39e49747be709977d7fba3c39b59f5575c40d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620502"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a>Sqlschemaexception teraz ustawia prawidłowo pozycje wierszy

#### <a name="details"></a>Szczegóły

Jeśli <xref:System.Xml.Linq.LoadOptions.SetLineInfo> wartość jest przenoszona do metody Load i wystąpi błąd walidacji, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> <xref:System.Xml.Schema.XmlSchemaException.LinePosition> właściwości i zawierają teraz informacje o wierszu.

#### <a name="suggestion"></a>Sugestia

Kod obsługi wyjątków, który przyjmuje <xref:System.Xml.Schema.XmlSchemaException.LineNumber> i <xref:System.Xml.Schema.XmlSchemaException.LinePosition> nie zostanie ustawiony, należy zaktualizować, ponieważ te właściwości będą teraz prawidłowo ustawione, gdy SetLineInfo jest używany podczas ładowania kodu XML.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
