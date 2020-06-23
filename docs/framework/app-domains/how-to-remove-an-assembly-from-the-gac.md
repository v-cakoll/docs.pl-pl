---
title: 'Instrukcje: Usuwanie zestawu z globalnej pamięci podręcznej zestawów'
description: Informacje o usuwaniu zestawu z globalnej pamięci podręcznej zestawów w programie .NET przy użyciu narzędzia globalnej pamięci podręcznej zestawów (Gacutil.exe) lub Instalator Windows.
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
ms.openlocfilehash: e3a596ea6029ded190c33032e96b601de9d4012d
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104773"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a>Instrukcje: Usuwanie zestawu z globalnej pamięci podręcznej zestawów

Istnieją dwa sposoby usuwania zestawu z globalnej pamięci podręcznej zestawów (GAC):

- Za pomocą [Narzędzia globalnej pamięci podręcznej zestawów (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md). Za pomocą tej opcji można odinstalować zestawy, które zostały umieszczone w pamięci GAC podczas tworzenia i testowania.

- Za pomocą [Instalator Windows](/windows/desktop/Msi/windows-installer-portal). Tej opcji należy używać do odinstalowywania zestawów podczas testowania pakietów instalacyjnych i systemów produkcyjnych.

## <a name="removing-an-assembly-with-gacutilexe"></a>Usuwanie zestawu z Gacutil.exe

W wierszu polecenia wpisz następujące polecenie:

**Gacutil – u**\<*assembly name*>

W tym poleceniu *Nazwa zestawu* to nazwa zestawu, który ma zostać usunięty z globalnej pamięci podręcznej zestawów.

> [!WARNING]
> Nie należy używać Gacutil.exe do usuwania zestawów w systemach produkcyjnych ze względu na możliwość, że zestaw nadal może być wymagany przez niektóre aplikacje. Zamiast tego należy użyć Instalator Windows, która zachowuje liczbę odwołań dla każdego zestawu instalowanego w pamięci podręcznej GAC.

Poniższy przykład usuwa zestaw o nazwie `hello.dll` z globalnej pamięci podręcznej zestawów:

```console
gacutil -u hello
```

## <a name="removing-an-assembly-with-windows-installer"></a>Usuwanie zestawu z Instalator Windows

W aplikacji **programy i funkcje** w **Panelu sterowania**wybierz aplikację, którą chcesz odinstalować. Jeśli pakiet instalacyjny zawiera zestawy w pamięci podręcznej GAC, Instalator Windows usunie je, jeśli nie są używane przez inną aplikację.

> [!NOTE]
> Instalator Windows utrzymuje liczbę odwołań dla zestawów zainstalowanych w pamięci podręcznej GAC. Zestaw jest usuwany z pamięci GAC tylko wtedy, gdy jego licznik odwołań osiągnie wartość zero, co oznacza, że nie jest używany przez żadną aplikację zainstalowaną przez pakiet Instalator Windows.

## <a name="see-also"></a>Zobacz też

- [Praca z zestawami i globalną pamięcią podręczną zestawów](working-with-assemblies-and-the-gac.md)
- [Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](install-assembly-into-gac.md)
- [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md)
