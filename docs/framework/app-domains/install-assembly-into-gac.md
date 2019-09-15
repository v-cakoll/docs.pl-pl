---
title: 'Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej zestawów'
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de5ae03ab885c4368e39b6339b5a14d1082e6df5
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972936"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej zestawów

Global Assembly Cache (GAC) przechowuje zestawy, które są udostępniane przez kilka aplikacji. Zainstaluj zestaw w [globalnej pamięci podręcznej zestawów](gac.md) przy użyciu jednego z następujących składników: 

- [Windows Installer](#windows-installer)
- [Narzędzie globalnej pamięci podręcznej zestawów](#global-assembly-cache-tool)

> [!IMPORTANT]
> Można zainstalować tylko zestawy o silnych nazwach w globalnej pamięci podręcznej zestawów. Informacje o sposobie tworzenia zestawu o silnej nazwie można znaleźć w temacie [How to: Podpisz zestaw silną nazwą](../../standard/assembly/sign-strong-name.md).

## <a name="windows-installer"></a>Instalator Windows

[Instalator Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), aparat instalacji systemu Windows, jest zalecanym sposobem dodawania zestawów do globalnej pamięci podręcznej zestawów. Instalator Windows zapewnia zliczanie odwołań zestawów w globalnej pamięci podręcznej zestawów i inne korzyści. Aby utworzyć pakiet Instalatora dla Instalator Windows, użyj rozszerzenia zestawu [narzędzi WIX dla programu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

## <a name="global-assembly-cache-tool"></a>Narzędzie Global Assembly Cache

Aby dodać zestawy do globalnej pamięci podręcznej zestawów i wyświetlić zawartość globalnej pamięci podręcznej zestawów, można użyć [Narzędzia globalnej pamięci podręcznej zestawów platformy .NET (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) .

   > [!NOTE]
   > *Gacutil. exe* służy tylko do celów deweloperskich. Nie należy używać go do instalowania zestawów produkcyjnych w globalnej pamięci podręcznej zestawów.

Składnia programu *Gacutil. exe* do zainstalowania zestawu w pamięci podręcznej jest następująca:

```cmd
gacutil -i <assembly name>
```

W tym poleceniu  *\<nazwa zestawu >* jest nazwą zestawu, który ma zostać zainstalowany w globalnej pamięci podręcznej zestawów.

Jeśli *Gacutil. exe* nie znajduje się w ścieżce systemu, należy użyć [wiersza polecenia dewelopera dla programu vs  *\<w wersji >* ](../tools/developer-command-prompt-for-vs.md).

Poniższy przykład instaluje zestaw z nazwą pliku *Hello. dll* w globalnej pamięci podręcznej zestawów.

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> We wcześniejszych wersjach .NET Framework rozszerzenie powłoki systemu Windows *Shfusion. dll* umożliwia instalowanie zestawów przez przeciąganie ich do Eksploratora plików. Począwszy od .NET Framework 4 *Shfusion. dll* jest przestarzały.

## <a name="see-also"></a>Zobacz także

- [Pracuj z zestawami i globalną pamięcią podręczną zestawów](working-with-assemblies-and-the-gac.md)
- [Instrukcje: Usuwanie zestawu z globalnej pamięci podręcznej zestawów](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil. exe (Narzędzie globalnej pamięci podręcznej zestawów)](../tools/gacutil-exe-gac-tool.md)
- [Instrukcje: Podpisz zestaw silną nazwą](../../standard/assembly/sign-strong-name.md)
