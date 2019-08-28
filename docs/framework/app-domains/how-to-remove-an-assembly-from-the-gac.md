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
ms.openlocfilehash: 7c66df518a259e57498e31877b2f1a78657e05bc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040815"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a>Instrukcje: Usuwanie zestawu z globalnej pamięci podręcznej zestawów

Istnieją dwa sposoby usuwania zestawu z globalnej pamięci podręcznej zestawów (GAC):

- Za pomocą [Narzędzia globalnej pamięci podręcznej zestawów (Gacutil. exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md). Za pomocą tej opcji można odinstalować zestawy, które zostały umieszczone w pamięci GAC podczas tworzenia i testowania.

- Za pomocą [Instalator Windows](/windows/desktop/Msi/windows-installer-portal). Tej opcji należy używać do odinstalowywania zestawów podczas testowania pakietów instalacyjnych i systemów produkcyjnych.

### <a name="removing-an-assembly-with-gacutilexe"></a>Usuwanie zestawu za pomocą gacutil. exe

1. W wierszu polecenia wpisz następujące polecenie:

    **Gacutil – u** \< *Nazwa zestawu*>

    W tym poleceniu *Nazwa zestawu* to nazwa zestawu, który ma zostać usunięty z globalnej pamięci podręcznej zestawów.

    > [!WARNING]
    > Nie należy używać programu Gacutil. exe do usuwania zestawów w systemach produkcyjnych ze względu na możliwość, że zestaw nadal może być wymagany przez niektóre aplikacje. Zamiast tego należy użyć Instalator Windows, która zachowuje liczbę odwołań dla każdego zestawu instalowanego w pamięci podręcznej GAC.

 Poniższy przykład usuwa zestaw o nazwie `hello.dll` z globalnej pamięci podręcznej zestawów.

```
gacutil -u hello
```

### <a name="removing-an-assembly-with-windows-installer"></a>Usuwanie zestawu z Instalator Windows

1. W aplikacji **programy i funkcje** w **Panelu sterowania**wybierz aplikację, którą chcesz odinstalować. Jeśli pakiet instalacyjny zawiera zestawy w pamięci podręcznej GAC, Instalator Windows usunie je, jeśli nie są używane przez inną aplikację.

    > [!NOTE]
    > Instalator Windows utrzymuje liczbę odwołań dla zestawów zainstalowanych w pamięci podręcznej GAC. Zestaw jest usuwany z pamięci GAC tylko wtedy, gdy jego licznik odwołań osiągnie wartość zero, co oznacza, że nie jest używany przez żadną aplikację zainstalowaną przez pakiet Instalator Windows.

## <a name="see-also"></a>Zobacz także

- [Praca z zestawami i globalną pamięcią podręczną zestawów](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)
- [Gacutil.exe (narzędzie Global Assembly Cache)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
