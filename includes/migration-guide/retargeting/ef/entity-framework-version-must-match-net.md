---
ms.openlocfilehash: 4c6a89f9753989a5ad061e847dff70d2af0b3cf4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774424"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a>Entity Framework w wersji musi odpowiadać wersji programu .NET Framework

|   |   |
|---|---|
|Szczegóły|Programu entity framework w wersji powinny zostać dopasowane do wersji programu .NET framework. Entity Framework 5 jest zalecane dla platformy .NET Framework 4.5. Istnieje kilka znanych problemów z programem EF 4.x w projekcie programu .NET Framework 4.5 wokół <xref:System.ComponentModel.DataAnnotations>. W .NET 4.5 te zostały przeniesione do innego zestawu, dzięki czemu nie występują problemy, określająca, które adnotacje do użycia.|
|Sugestia|Uaktualnianie do programu Entity Framework 5 dla programu .NET Framework 4.5|
|Zakres|Duży|
|Wersja|4.5|
|Typ|Przekierowanie|
