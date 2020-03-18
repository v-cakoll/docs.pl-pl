---
title: Optymalizacja udostępnionej usługi hostingu sieci Web
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: 07a100e2cd6aaff2b54b99144c9d762c8979fb47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140273"
---
# <a name="optimization-for-shared-web-hosting"></a>Optymalizacja udostępnionej usługi hostingu sieci Web
Jeśli jesteś administratorem serwera współdzielonego przez hostowanie kilku małych witryn sieci Web, możesz `gcTrimCommitOnLowMemory` zoptymalizować wydajność i zwiększyć pojemność lokacji, dodając następujące ustawienie do `runtime` węzła w pliku Aspnet.config w katalogu .NET:  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> To ustawienie jest zalecane tylko w przypadku scenariuszy hostingu udostępnionego sieci Web.  
  
 Ponieważ moduł zbierający elementy bezużyteczne zachowuje pamięć dla przyszłych alokacji, jego zatwierdzone miejsce może być więcej niż to, co jest ściśle potrzebne. Można zmniejszyć to miejsce, aby pomieścić razy, gdy istnieje duże obciążenie pamięci systemowej. Zmniejszenie tej zaangażowanej przestrzeni zwiększa wydajność i zwiększa pojemność hostowania większej liczby witryn.  
  
 Gdy `gcTrimCommitOnLowMemory` ustawienie jest włączone, moduł zbierający elementy bezużyteczne ocenia obciążenie pamięci systemowej i przechodzi w tryb przycinania, gdy obciążenie osiągnie 90%. Utrzymuje tryb przycinania, aż obciążenie spadnie poniżej 85%.  
  
 Gdy pozwalają na to warunki, moduł `gcTrimCommitOnLowMemory` zbierający elementy bezużyteczne może zdecydować, że ustawienie nie pomoże bieżącej aplikacji i zignorować go.  
  
## <a name="example"></a>Przykład  
 Poniższy fragment XML pokazuje, `gcTrimCommitOnLowMemory` jak włączyć ustawienie. Elipsy wskazują inne ustawienia, `runtime` które byłyby w węźle.  
  
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

- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
