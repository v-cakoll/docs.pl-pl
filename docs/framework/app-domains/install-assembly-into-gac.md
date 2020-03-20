---
title: 'Jak: Instalowanie zestawu w globalnej pamięci podręcznej zestawów'
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 64878a795a7c5b790c8991064e32b82505685c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155566"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Jak: Instalowanie zestawu w globalnej pamięci podręcznej zestawów

Globalna pamięć podręczna zestawów (GAC) przechowuje zestawy współużytkowane przez kilka aplikacji. Zainstaluj zespół w [globalnej pamięci podręcznej zestawów](gac.md) z jednym z następujących składników:

- [Instalator Windows](#windows-installer)
- [Narzędzie Globalna pamięć podręczna zestawów](#global-assembly-cache-tool)

> [!IMPORTANT]
> W globalnej pamięci podręcznej zestawów można zainstalować tylko zestawy o silnych nazwach. Aby uzyskać informacje dotyczące tworzenia zestawu o silnej nazwie, zobacz [Jak: Podpisz zestaw o silnej nazwie](../../standard/assembly/sign-strong-name.md).

## <a name="windows-installer"></a>Instalator Windows

[Instalator Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), aparat instalacji systemu Windows, jest zalecanym sposobem dodawania zestawów do globalnej pamięci podręcznej zestawów. Instalator Windows zapewnia zliczanie odwołań zestawów w globalnej pamięci podręcznej zestawów i inne korzyści. Aby utworzyć pakiet instalacyjny dla Instalatora Windows, użyj [rozszerzenia zestawu narzędzi WiX dla programu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

## <a name="global-assembly-cache-tool"></a>Narzędzie Globalna pamięć podręczna zestawów

Za pomocą [narzędzia .NET Global Assembly Cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) można dodać zestawy do globalnej pamięci podręcznej zestawów i wyświetlić zawartość globalnej pamięci podręcznej zestawów.

   > [!NOTE]
   > *Gacutil.exe* służy wyłącznie do celów rozwojowych. Nie używaj go do instalowania zestawów produkcyjnych w globalnej pamięci podręcznej zestawów.

Składnia za pomocą *gacutil.exe* do zainstalowania zestawu w gac jest następująca:

```cmd
gacutil -i <assembly name>
```

W tym * \<poleceniu nazwa zestawu>* jest nazwą zestawu do zainstalowania w globalnej pamięci podręcznej zestawów.

Jeśli *pliku gacutil.exe* nie ma w ścieżce systemowej, użyj [wiersza polecenia Deweloper dla wersji programu VS * \<>* ](../tools/developer-command-prompt-for-vs.md).

Poniższy przykład instaluje zestaw o nazwie pliku *hello.dll* w globalnej pamięci podręcznej zestawów.

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> We wcześniejszych wersjach programu .NET Framework rozszerzenie powłoki *shfusion.dll* systemu Windows umożliwia instalowanie zestawów przez przeciąganie ich do Eksploratora plików. Począwszy od programu .NET Framework 4, *shfusion.dll* jest przestarzały.

## <a name="see-also"></a>Zobacz też

- [Praca z zestawami i globalną pamięcią podręczną zestawów](working-with-assemblies-and-the-gac.md)
- [Jak: Usuwanie zestawu z globalnej pamięci podręcznej zestawów](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (narzędzie Globalna pamięć podręczna zestawów)](../tools/gacutil-exe-gac-tool.md)
- [Jak: Podpisz zestaw o silnej nazwie](../../standard/assembly/sign-strong-name.md)
