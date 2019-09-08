---
title: Środki zaradcze Układ WPF
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d266ad33110d2bda8f7911d89981c372624c3f36
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779065"
---
# <a name="mitigation-wpf-layout"></a>Środki zaradcze Układ WPF
Układ formantów WPF może się nieco zmieniać.  
  
## <a name="impact"></a>Wpływ  
 W wyniku tej zmiany:  
  
- Szerokość lub wysokość elementów może wzrosnąć lub zmniejszyć o co najwyżej jeden piksel.  
  
- Położenie obiektu może zostać przeniesione o co najwyżej jeden piksel.  
  
- Wyśrodkowane elementy mogą być przesunięte w pionie lub w poziomie o co najwyżej jeden piksel.  
  
 Domyślnie ten nowy układ jest włączony tylko dla aplikacji przeznaczonych dla .NET Framework 4,6.  
  
## <a name="mitigation"></a>Ograniczenie  
 Ponieważ ta modyfikacja ma na celu wyeliminowanie wycinków prawej lub dolnej części formantów WPF o wysokiej rozdzielczościami, aplikacje, które są przeznaczone dla wcześniejszych wersji .NET Framework ale działają na .NET Framework 4,6, mogą przystąpić do tego nowego zachowania, dodając następujący wiersz do `<runtime>` sekcja pliku App. config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 Aplikacje, które są przeznaczone dla .NET Framework 4,6, ale chcą, aby formanty WPF mogły być renderowane przy użyciu poprzedniego algorytmu układu, można to zrobić `<runtime>` , dodając następujący wiersz do sekcji pliku App. config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](retargeting-changes-in-the-net-framework-4-6.md)
