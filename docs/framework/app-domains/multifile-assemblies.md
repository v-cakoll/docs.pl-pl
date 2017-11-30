---
title: Zestawy wieloplikowe
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fead0a944b464ffd8f72dca6da33fd97404fe2d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="multifile-assemblies"></a>Zestawy wieloplikowe
Możesz utworzyć wiele plików zestawów przy użyciu kompilatory w wierszu polecenia lub [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] z programem Visual C++. Jeden plik w zestawie musi zawierać manifest zestawu. Zestaw, który uruchamia aplikację musi również zawierać punkt wejścia, takich jak metoda Main lub WinMain.  
  
 Na przykład załóżmy, że masz aplikację, która zawiera dwa moduły kodu, Client.cs i Stringer.cs. Tworzy Stringer.cs `myStringer` przestrzeni nazw, która odwołuje się do niego kod w Client.cs. Zawiera Client.cs `Main` metodę, która jest punkt wejścia aplikacji. W tym przykładzie skompilować modułów dwóch kodu, a następnie utwórz trzeci plik, który zawiera manifest zestawu, który uruchamia aplikację. Manifest zestawu odwołuje się do obu `Client` i `Stringer` modułów.  
  
> [!NOTE]
>  Zestawy wieloplikowe może mieć tylko jeden wpis punktu, nawet jeśli zestaw ma wiele modułów kodu.  
  
 Istnieje kilka przyczyn, które można utworzyć zestawu wieloplikowego:  
  
-   Aby połączyć modułów napisane w różnych językach. Jest to najbardziej typowe przyczyny utworzenia zestawu wieloplikowego.  
  
-   Aby zoptymalizować pobieranie aplikacji przez umieszczenie rzadko używane typy w module, który jest pobierany tylko wtedy, gdy potrzebne.  
  
    > [!NOTE]
    >  Jeśli tworzysz aplikacje, które zostaną pobrane przy użyciu `<object>` tagu z programem Microsoft Internet Explorer jest ważne, aby utworzyć zestawy wieloplikowe. W tym scenariuszu utworzysz plik oddzielony od własnych modułów kodu, które zawiera manifest zestawu. Program Internet Explorer pliki do pobrania manifest zestawu, a następnie tworzy wątków roboczych, aby pobrać wszystkie dodatkowe moduły lub zestawy wymagane. Podczas pobierania pliku manifestu zestawu zawierającego, program Internet Explorer będzie odpowiadać na dane wejściowe użytkownika. Mniejsze pliku manifestu zestawu zawierającego mniej czasu programu Internet Explorer będzie odpowiadać.  
  
-   Aby połączyć utworzona przez deweloperów kilka modułów kodu. Mimo że każdy deweloper może skompilować poszczególnych modułów kodu w zespół, to wymuszenie niektóre typy uwidocznienia publicznie, które nie są dostępne, jeśli wszystkie moduły są umieszczane w zestawów wieloplikowych.  
  
 Po utworzeniu zestawu, możesz utworzyć plik, który zawiera manifest zestawu (a tym samym zestawie), lub możesz nadać silnej nazwy pliku (i zestawu) i umieścić go w pamięci podręcznej GAC.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: kompilacja zestawów wieloplikowych](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
