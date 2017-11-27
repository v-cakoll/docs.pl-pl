---
title: "Porady: usuwanie zestawu z globalnej pamięci podręcznej zestawów"
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
- Gacutil.exe
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a17478c350d789d320e97d6b50d6f5f9daaf6db3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a>Porady: usuwanie zestawu z globalnej pamięci podręcznej zestawów
Istnieją dwa sposoby usuwanie zestawu z globalnej pamięci podręcznej zestawów (GAC):  
  
-   Za pomocą [narzędzie Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md). Ta opcja umożliwia odinstalowanie zestawy, które zostały umieszczone w pamięci GAC podczas projektowania i testowania.  
  
-   Za pomocą [Instalatora Windows](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx). Tej opcji należy używać do odinstalowania zestawy podczas testowania pakietów instalacyjnych, a dla systemów produkcyjnych.  
  
### <a name="removing-an-assembly-with-gacutilexe"></a>Usuwanie zestawu z Gacutil.exe  
  
1.  W wierszu polecenia wpisz następujące polecenie:  
  
     **Gacutil – u** \< *nazwy zestawu*>  
  
     W tym poleceniu *nazwy zestawu* jest nazwą zestawu, aby usunąć z pamięci podręcznej GAC.  
  
    > [!WARNING]
    >  Nie należy używać Gacutil.exe można usunąć zestawów w systemach produkcyjnych z powodu możliwości zestawu nadal mogą być wymagane przez aplikację. Zamiast tego należy użyć Instalatora systemu Windows, który obsługuje liczba odwołań dla każdego zestawu, który instaluje go w pamięci GAC.  
  
 Poniższy przykład umożliwia usunięcie zestawu o nazwie `hello.dll` z globalnej pamięci podręcznej zestawów.  
  
```  
gacutil -u hello  
```  
  
### <a name="removing-an-assembly-with-windows-installer"></a>Usuwanie zestawu z Instalatora Windows  
  
1.  Z **programy i funkcje** aplikacji w **Panelu sterowania**, wybierz aplikację, którą chcesz odinstalować. Jeśli pakiet instalacyjny zestawy są umieszczane w pamięci GAC, Instalator systemu Windows będzie je usunąć, jeśli nie są używane przez inną aplikację.  
  
    > [!NOTE]
    >  Instalator systemu Windows obsługuje liczba odwołań dla zestawów zainstalowanych w pamięci GAC. Zestaw zostanie usunięty z pamięci podręcznej GAC tylko wtedy, gdy jego liczebności referencyjnej osiągnie zero, co oznacza, że nie jest używany przez wszelkie aplikacje zainstalowane przez pakiet Instalatora Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z zestawami i Globalna pamięć podręczna zestawów](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Porady: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [Gacutil.exe (narzędzie Global Assembly Cache)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
