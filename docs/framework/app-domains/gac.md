---
title: Global Assembly Cache
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eedb33042bd904340cc02526c3f1cf927c09bd9c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="global-assembly-cache"></a>Global Assembly Cache
Każdy komputer, na którym zainstalowano środowisko uruchomieniowe języka wspólnego używa pamięci podręcznej kodu dla komputera o nazwie Global Assembly Cache. Global Assembly Cache przechowuje zestawy wyznaczonych być współużytkowane przez kilka aplikacji na komputerze.  
  
 Zestawy powinny współużytkować przez zainstalowanie ich w globalnej pamięci podręcznej zestawów, tylko wtedy, gdy jest to konieczne. Generalnie zachowywać prywatność zestawów i lokalizowanie zestawów w katalogu aplikacji, chyba że jawnie wymagana jest udostępnianie zestawu. Ponadto nie jest konieczne zainstalowanie zestawów w globalnej pamięci podręcznej zestawów, aby udostępnić COM interop lub kodu niezarządzanego.  
  
> [!NOTE]
>  Istnieją scenariusze, w którym jawnie nie chcesz instalować zestawów w globalnej pamięci podręcznej zestawów. Jeśli jeden z zestawów, które tworzą aplikację w globalnej pamięci podręcznej zestawów, może już replikacji lub zainstalować aplikację przy użyciu **xcopy** polecenie, aby skopiować z katalogu aplikacji. Należy przenieść zestawu w globalnej pamięci podręcznej zestawów również.  
  
 Istnieją dwa sposoby wdrożenia zestawu w globalnej pamięci podręcznej zestawów:  
  
-   Użyj Instalatora zaprojektowane do pracy z globalnej pamięci podręcznej zestawów. Jest to preferowaną opcję instalowania zestawów w globalnej pamięci podręcznej zestawów.  
  
-   Za pomocą narzędzia Projektant o nazwie [narzędzie Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), podany przez [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
    > [!NOTE]
    >  W scenariuszach wdrażania za pomocą Instalatora Windows zainstaluj zestawów w globalnej pamięci podręcznej zestawów. Narzędzie Global Assembly Cache tylko w przypadku scenariuszy programowania, ponieważ nie zawiera on liczenie odwołań zestawu i inne funkcje podany przy wywołaniu metody za pomocą Instalatora Windows.  
  
 Począwszy od programu .NET Framework 4, jest domyślną lokalizacją Global Assembly Cache **%windir%\Microsoft.NET\assembly**. We wcześniejszych wersjach programu .NET Framework, domyślna lokalizacja to **%windir%\assembly**.  
  
 Administratorzy często chronią katalog do kontrolowania zapisu i wykonywania dostępu za pomocą listy kontroli dostępu (ACL). Ponieważ Global Assembly Cache jest instalowany w podkatalogu w katalogu systemowym, dziedziczy ACL tego katalogu. Zaleca się, że tylko użytkownicy z uprawnieniami administratora można usunąć pliki z globalnej pamięci podręcznej zestawów.  
  
 Zestawy wdrożone w globalnej pamięci podręcznej zestawów musi mieć silnej nazwy. Zestaw został dodany do globalnej pamięci podręcznej zestawów, sprawdzania integralności są wykonywane na wszystkie pliki wchodzące w skład zestawu. Pamięć podręczna wykonuje te testy integralności, aby upewnić się, że zestaw nie został zmodyfikowany, na przykład, gdy plik został zmieniony, ale manifest nie odzwierciedla zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Praca z zestawami i globalną pamięcią podręczną zestawów](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md)
