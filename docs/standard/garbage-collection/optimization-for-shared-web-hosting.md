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
ms.openlocfilehash: 7831e383a3048523909b79ac5a4706f3c1c48371
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45595363"
---
# <a name="optimization-for-shared-web-hosting"></a>Optymalizacja udostępnionej usługi hostingu sieci Web
Jeśli jesteś administratorem serwera, który jest współużytkowany przez kilka małych witryn sieci Web hostingu, można zoptymalizować wydajność i zwiększyć wydajność witryny, dodając następujące `gcTrimCommitOnLowMemory` ustawienie `runtime` węzeł w pliku konfigurację Aspnet.config na platformie .NET katalog:  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  To ustawienie jest zalecane tylko dla udostępnionych w sieci Web w scenariuszach hostingu.  
  
 Ponieważ moduł odśmiecania pamięci zachowuje pamięć dla przyszłej alokacji, może być jej przydzielonych miejsc, więcej niż ściśle potrzebne. Można zmniejszyć tego miejsca, aby pomieścić godziny po duże obciążenie pamięci systemowej. Zmniejszenie tego przydzielone miejsce zapewnia lepszą wydajność i rozwija zdolności do hostowania więcej witryn.  
  
 Gdy `gcTrimCommitOnLowMemory` ustawienie jest włączone, moduł zbierający elementy bezużyteczne ocenia obciążenia pamięci systemu i przechodzi trybie przycinania, gdy obciążenie osiągnie 90%. Dopóki obciążenie spadnie poniżej 85%, obsługuje tryb przycinania.  
  
 Gdy warunki na to pozwalają, wyrzucanie elementów bezużytecznych może zdecydować, że `gcTrimCommitOnLowMemory` ustawienie nie zostanie pomocy bieżącej aplikacji i go zignorować.  
  
## <a name="example"></a>Przykład  
 Poniższy fragment XML przedstawiono sposób włączania `gcTrimCommitOnLowMemory` ustawienie. Wielokropek wskazywać inne ustawienia, które będą miały `runtime` węzła.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
