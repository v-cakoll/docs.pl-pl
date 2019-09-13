---
title: 'Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej zestawów'
ms.date: 02/05/2019
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
ms.openlocfilehash: 8e2d051cda9861da1af2caa65160b6e753b24bd1
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926517"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej zestawów

Global Assembly Cache (GAC) przechowuje zestawy, które są udostępniane przez kilka aplikacji. Zainstaluj zestaw w [globalnej pamięci podręcznej zestawów](gac.md) przy użyciu jednego z następujących składników: 

- [Windows Installer](#windows-installer)
- [Narzędzie globalnej pamięci podręcznej zestawów](#global-assembly-cache-tool)

> [!IMPORTANT]
> Do pamięci podręcznej GAC można zainstalować tylko zestawy o silnych nazwach. Informacje o sposobie tworzenia zestawu o silnej nazwie można znaleźć w temacie [How to: Podpisz zestaw silną nazwą](how-to-sign-an-assembly-with-a-strong-name.md).

## <a name="windows-installer"></a>Instalator Windows

[Instalator Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), aparat instalacji systemu Windows, jest zalecanym sposobem dodawania zestawów do globalnej pamięci podręcznej zestawów. Instalator Windows zapewnia zliczanie odwołań zestawów w globalnej pamięci podręcznej zestawów i inne korzyści. Aby utworzyć pakiet Instalatora dla Instalator Windows, użyj rozszerzenia zestawu [narzędzi WIX dla programu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

## <a name="global-assembly-cache-tool"></a>Narzędzie globalnej pamięci podręcznej zestawów

Aby dodać zestawy do globalnej pamięci podręcznej zestawów i wyświetlić zawartość globalnej pamięci podręcznej zestawów, można użyć [Narzędzia globalnej pamięci podręcznej zestawów (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) .

   > [!NOTE]
   > *Gacutil. exe* służy tylko do celów deweloperskich. Nie należy używać go do instalowania zestawów produkcyjnych w globalnej pamięci podręcznej zestawów.

Składnia programu *Gacutil. exe* do zainstalowania zestawu w pamięci podręcznej jest następująca:

```console
gacutil -i <assembly name>
```

W tym poleceniu  *\<nazwa zestawu >* jest nazwą zestawu, który ma zostać zainstalowany w globalnej pamięci podręcznej zestawów.

Jeśli *Gacutil. exe* nie znajduje się w ścieżce systemowej, użyj [wiersz polecenia dla deweloperów dla programu vs  *\<version >* ](../tools/developer-command-prompt-for-vs.md).

Poniższy przykład instaluje zestaw z nazwą pliku *Hello. dll* w globalnej pamięci podręcznej zestawów.

```console
gacutil -i hello.dll
```

> [!NOTE]
> We wcześniejszych wersjach .NET Framework rozszerzenie powłoki systemu Windows *Shfusion. dll* umożliwia instalowanie zestawów przez przeciąganie ich do Eksploratora plików. Począwszy od .NET Framework 4 *Shfusion. dll* jest przestarzały.

## <a name="see-also"></a>Zobacz także

- [Praca z zestawami i globalną pamięcią podręczną zestawów](working-with-assemblies-and-the-gac.md)
- [Instrukcje: Usuwanie zestawu z globalnej pamięci podręcznej zestawów](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil. exe (Narzędzie globalnej pamięci podręcznej zestawów)](../tools/gacutil-exe-gac-tool.md)
- [Instrukcje: Podpisz zestaw silną nazwą](how-to-sign-an-assembly-with-a-strong-name.md)
