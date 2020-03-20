---
title: 'Ograniczenie: układ platformy WPF'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: 7a074698fd203d0c5f9b799bfee8a6a9cb40800e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457784"
---
# <a name="mitigation-wpf-layout"></a>Ograniczenie: układ platformy WPF
Układ formantów WPF można zmienić nieznacznie.  
  
## <a name="impact"></a>Wpływ  
 W wyniku tej zmiany:  
  
- Szerokość lub wysokość elementów może rosnąć lub zmniejszać się o co najwyżej jeden piksel.  
  
- Położenie obiektu może poruszać się o co najwyżej jeden piksel.  
  
- Wyśrodkowane elementy mogą być pionowo lub poziomo wyłączone do środka o co najwyżej jeden piksel.  
  
 Domyślnie ten nowy układ jest włączony tylko dla aplikacji, które są przeznaczone dla programu .NET Framework 4.6.  
  
## <a name="mitigation"></a>Środki zaradcze  
 Ponieważ ta modyfikacja ma tendencję do wyeliminowania przycinania prawego lub dolnego poziomu formantów WPF w wysokich dpis, aplikacje, które są przeznaczone dla wcześniejszych wersji `<runtime>` programu .NET Framework, ale są uruchomione w programie .NET Framework 4.6, mogą zdecydować się na to nowe zachowanie, dodając następujący wiersz do sekcji pliku app.config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 Aplikacje, które są przeznaczone dla programu .NET Framework 4.6, ale chcesz, aby formanty WPF renderowane przy użyciu poprzedniego algorytmu układu można to zrobić, dodając następujący wiersz do `<runtime>` sekcji pliku app.config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
