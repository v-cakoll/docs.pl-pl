---
title: 'Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej'
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
ms.openlocfilehash: 233a7803cb59f9bfeac15d293dc3fb5a0db449c9
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903758"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej

Zestawy, które mają kilka aplikacji są przechowywane w globalnej pamięci podręcznej zestawów (GAC). Instalowanie zestawu w [globalnej pamięci podręcznej](gac.md) przy użyciu jednego z następujących składników: 
- [Windows Installer](#windows-installer)
- [Narzędzie Global assembly cache](#global-assembly-cache-tool)

> [!IMPORTANT]
> Pamięci podręcznej GAC można instalować tylko zestawy o silnych nazwach. Aby uzyskać informacje o sposobie tworzenia zestawu z silną nazwą, zobacz [jak: Podpisywanie zestawu silną nazwą](how-to-sign-an-assembly-with-a-strong-name.md).

## <a name="windows-installer"></a>Instalator Windows

[Instalator Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), aparat instalacji Windows jest zalecany sposób dodawania zestawów do globalnej pamięci podręcznej. Instalator Windows zapewnia zliczanie odwołań zestawów w globalnej pamięci podręcznej i inne korzyści. Aby utworzyć pakiet instalacyjny Instalatora Windows, użyj [WiX rozszerzenia narzędzi programu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

## <a name="global-assembly-cache-tool"></a>Narzędzie Global assembly cache

Możesz użyć [narzędzie global assembly cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) dodawania zestawów do globalnej pamięci podręcznej oraz wyświetlanie zawartości globalnej pamięci podręcznej.

   > [!NOTE]
   > *Gacutil.exe* jest tylko do celów programowania. Nie jest używany do instalowania zestawów produkcyjnych w globalnej pamięci podręcznej.

Składnia przy użyciu *gacutil.exe* instalować zestawów w globalnej pamięci podręcznej zestawów jest następująca:

```console
gacutil -i <assembly name>
```

W tym poleceniu  *\<Nazwa zestawu >* to nazwa zestawu, aby zainstalować w globalnej pamięci podręcznej.

Jeśli *gacutil.exe* nie znajduje się w ścieżce systemowej, użyj [wiersz polecenia programisty dla programu VS  *\<wersji >*](../tools/developer-command-prompt-for-vs.md).

Poniższy przykład instaluje zestaw o nazwie pliku *hello.dll* w globalnej pamięci podręcznej.

```console
gacutil -i hello.dll
```

> [!NOTE]
> We wcześniejszych wersjach programu .NET Framework *Shfusion.dll* rozszerzenie powłoki Windows umożliwiają instalowanie zestawów, przeciągając je do Eksploratora plików. Począwszy od programu .NET Framework 4, *Shfusion.dll* jest przestarzały.

## <a name="see-also"></a>Zobacz także

- [Praca z zestawami i globalną pamięcią podręczną zestawów](working-with-assemblies-and-the-gac.md)
- [Instrukcje: Usuwanie zestawu z globalnej pamięci podręcznej](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (narzędzie Global assembly cache)](../tools/gacutil-exe-gac-tool.md)
- [Instrukcje: Podpisywanie zestawu silną nazwą](how-to-sign-an-assembly-with-a-strong-name.md)
