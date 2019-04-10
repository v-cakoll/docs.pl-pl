---
title: 'Instrukcje: Usuwanie zestawu z globalnej pamięci podręcznej zestawów'
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff00e2f1d266243f0453f004564f2ed802d26c85
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338725"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a>Instrukcje: Usuwanie zestawu z globalnej pamięci podręcznej zestawów
Istnieją dwa sposoby, aby usunąć zestaw z globalnej pamięci podręcznej zestawów (GAC):  
  
-   Za pomocą [narzędzia Globalna pamięć podręczna zestawów (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md). Ta opcja służy do odinstalowania zestawów, które zostały umieszczone w pamięci podręcznej GAC, podczas opracowywania i testowania.  
  
-   Za pomocą [Instalatora Windows](/windows/desktop/Msi/windows-installer-portal). Tej opcji należy używać do odinstalowania zestawów podczas testowania pakietów instalacyjnych, a dla systemów produkcyjnych.  
  
### <a name="removing-an-assembly-with-gacutilexe"></a>Usuwanie zestawu z Gacutil.exe  
  
1. W wierszu polecenia wpisz następujące polecenie:  
  
     **Gacutil – u** \< *nazwy zestawu*>  
  
     W tym poleceniu *nazwy zestawu* to nazwa zestawu, aby usunąć z globalnej pamięci podręcznej.  
  
    > [!WARNING]
    >  Nie należy używać Gacutil.exe można usunąć zestawów na systemy produkcyjne ze względu na możliwość, że zestaw nadal może być wymagane przez niektóre aplikacje. Zamiast tego należy użyć Instalatora Windows, który przechowuje licznik odwołań dla każdego zestawu, który instaluje go w pamięci GAC.  
  
 W następującym przykładzie usunięto zestaw o nazwie `hello.dll` z globalnej pamięci podręcznej.  
  
```  
gacutil -u hello  
```  
  
### <a name="removing-an-assembly-with-windows-installer"></a>Usuwanie zestawu za pomocą Instalatora Windows  
  
1. Z **programy i funkcje** aplikacji w **Panelu sterowania**, wybierz aplikację, która ma zostać odinstalowany. Jeśli pakiet instalacyjny umieszczone zestawów w pamięci podręcznej GAC, Instalator Windows spowoduje usunięcie ich, jeśli nie są one używane przez inną aplikację.  
  
    > [!NOTE]
    >  Instalator Windows przechowuje licznik odwołań do zestawów zainstalowane w GAC. Zestaw zostanie usunięty z pamięci podręcznej GAC, tylko wtedy, gdy jego licznik odwołań osiągnie zero, co oznacza, że nie jest używany przez dowolną aplikację, instalowane przez pakiet Instalatora Windows.  
  
## <a name="see-also"></a>Zobacz także

- [Praca z zestawami i globalną pamięcią podręczną zestawów](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Instrukcje: instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)
- [Gacutil.exe (Narzędzie Global Assembly Cache)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
