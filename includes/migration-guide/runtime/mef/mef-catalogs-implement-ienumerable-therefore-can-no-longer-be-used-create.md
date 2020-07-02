---
ms.openlocfilehash: 598df2121b480d411dac9c5571772a4a8d22b5ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620338"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>Wykazy MEF implementują interfejs IEnumerable i w związku z tym nie mogą być już używane do tworzenia serializatora

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,5, wykazy MEF implementują interfejs IEnumerable i w związku z tym nie można już używać do tworzenia serializatora ( <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> obiektu). Próba serializowania katalogu MEF powoduje zgłoszenie wyjątku.

#### <a name="suggestion"></a>Sugestia

Nie można już używać MEF do tworzenia serializatora

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Duży|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
