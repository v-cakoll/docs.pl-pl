---
ms.openlocfilehash: 4c6a89f9753989a5ad061e847dff70d2af0b3cf4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234812"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a>Entity Framework w wersji musi odpowiadać wersji programu .NET Framework

|   |   |
|---|---|
|Szczegóły|Programu entity framework w wersji powinny zostać dopasowane do wersji programu .NET framework. Entity Framework 5 jest zalecane dla platformy .NET Framework 4.5. Istnieje kilka znanych problemów z programem EF 4.x w projekcie programu .NET Framework 4.5 wokół <xref:System.ComponentModel.DataAnnotations>. W .NET 4.5 te zostały przeniesione do innego zestawu, dzięki czemu nie występują problemy, określająca, które adnotacje do użycia.|
|Sugestia|Uaktualnianie do programu Entity Framework 5 dla programu .NET Framework 4.5|
|Zakres|Duży|
|Wersja|4.5|
|Typ|Przekierowanie|
