---
title: 'Środki zaradcze: Układ platformy WPF'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c261a025548b2d22f6df3051dbcdb637723d4324
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599470"
---
# <a name="mitigation-wpf-layout"></a>Środki zaradcze: Układ platformy WPF
Nieco zmienić układ kontrolek WPF.  
  
## <a name="impact"></a>Wpływ  
 W wyniku tej zmiany:  
  
- Szerokość lub wysokość elementów może zwiększać i zmniejszać co najwyżej jeden piksel.  
  
- Położenie obiektu można przenieść co najwyżej jeden piksel.  
  
- Wyśrodkowany elementy mogą być w pionie lub w poziomie, od środka co najwyżej jeden piksel.  
  
 Domyślnie ten nowy układ jest włączona tylko dla aplikacji przeznaczonych dla platformy .NET Framework 4.6.  
  
## <a name="mitigation"></a>Ograniczenie  
 Ponieważ ta modyfikacja zwykle wyeliminować wycinka elementu po prawej stronie lub u dołu okna kontrolki WPF w dużych wysokiej, aplikacje docelowe wcześniejszych wersji programu .NET Framework, które są uruchomione na platformie .NET Framework 4.6 mogą wyrazić zgodę to nowe zachowanie, dodając następujący wiersz do `<runtime>` sekcji w pliku app.config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 Aplikacje, które docelowych programu .NET Framework 4.6, ale chcesz kontrolek WPF do renderowania przy użyciu poprzednich algorytmu układu można to zrobić, dodając następujący wiersz do `<runtime>` sekcji w pliku app.config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
