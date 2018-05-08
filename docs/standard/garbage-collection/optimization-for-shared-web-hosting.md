---
title: Optymalizacja udostępnionej usługi hostingu sieci Web
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3c979477f0928c9c3d2a393042867c84df33ecf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="optimization-for-shared-web-hosting"></a>Optymalizacja udostępnionej usługi hostingu sieci Web
Jeśli jesteś administratorem serwera, który jest współużytkowany przez hosting kilka małych witryn sieci Web można zoptymalizować wydajność i zwiększyć wydajność witryny, dodając następujące `gcTrimCommitOnLowMemory` ustawienie `runtime` węzeł w pliku konfigurację Aspnet.config w ramach platformy .NET katalog:  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  To ustawienie jest zalecane tylko dla udostępnionych w sieci Web w scenariuszach hostingu.  
  
 Ponieważ moduł garbage collector zachowuje pamięć dla przyszłych alokacji, jego przydzielone miejsce może być więcej niż ściśle potrzebna. Zmniejsza to miejsce, by uwzględnić czas po duże obciążenie pamięci systemowej. Zmniejsza to przydzielone miejsce poprawia wydajność i rozwija zdolności do obsługi więcej witryn.  
  
 Gdy `gcTrimCommitOnLowMemory` ustawienie jest włączone, moduł zbierający elementy bezużyteczne ocenia obciążenia pamięci systemu i przejdzie do trybu przycinanie podczas obciążenia wynosi 90%. Ta funkcja obsługuje tryb przycinanie dopóki obciążenia spadnie poniżej 85%.  
  
 Gdy zezwolenie na warunki, moduł zbierający elementy bezużyteczne można zdecydować, że `gcTrimCommitOnLowMemory` ustawienie nie zostanie pomocy bieżącej aplikacji i go zignorować.  
  
## <a name="example"></a>Przykład  
 Poniższy fragment XML pokazano, jak włączyć `gcTrimCommitOnLowMemory` ustawienie. Wielokropek wskazywać inne ustawienia, które byłyby w `runtime` węzła.  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
