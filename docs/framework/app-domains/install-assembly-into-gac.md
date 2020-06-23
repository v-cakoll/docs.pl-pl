---
title: 'Instrukcje: instalowanie zestawu w globalnej pamięci podręcznej zestawów'
description: Zainstaluj zestaw w globalnej pamięci podręcznej zestawów (GAC) w programie .NET, aby mógł być współużytkowany przez wiele aplikacji. Użyj Instalator Windows lub narzędzia GAC.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 08a5475d74327265f28b65676ae56be15afb57d3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104675"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Instrukcje: instalowanie zestawu w globalnej pamięci podręcznej zestawów

Global Assembly Cache (GAC) przechowuje zestawy, które są udostępniane przez kilka aplikacji. Zainstaluj zestaw w [globalnej pamięci podręcznej zestawów](gac.md) przy użyciu jednego z następujących składników:

- [Instalator Windows](#windows-installer)
- [Narzędzie globalnej pamięci podręcznej zestawów](#global-assembly-cache-tool)

> [!IMPORTANT]
> Można zainstalować tylko zestawy o silnych nazwach w globalnej pamięci podręcznej zestawów. Aby uzyskać informacje na temat sposobu tworzenia zestawu o silnej nazwie, zobacz [How to: Sign a Assembly with silnej nazwy](../../standard/assembly/sign-strong-name.md).

## <a name="windows-installer"></a>Instalator Windows

[Instalator Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), aparat instalacji systemu Windows, jest zalecanym sposobem dodawania zestawów do globalnej pamięci podręcznej zestawów. Instalator Windows zapewnia zliczanie odwołań zestawów w globalnej pamięci podręcznej zestawów i inne korzyści. Aby utworzyć pakiet Instalatora dla Instalator Windows, użyj rozszerzenia zestawu [narzędzi WIX dla programu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

## <a name="global-assembly-cache-tool"></a>Narzędzie globalnej pamięci podręcznej zestawów

Aby dodać zestawy do globalnej pamięci podręcznej zestawów i wyświetlić zawartość globalnej pamięci podręcznej zestawów, można użyć [Narzędzia do globalnej pamięci podręcznej zestawów .NET (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) .

   > [!NOTE]
   > *Gacutil.exe* służy tylko do celów deweloperskich. Nie należy używać go do instalowania zestawów produkcyjnych w globalnej pamięci podręcznej zestawów.

Składnia *gacutil.exe* służąca do instalowania zestawu w pamięci podręcznej GAC jest następująca:

```cmd
gacutil -i <assembly name>
```

W tym poleceniu *\<assembly name>* jest nazwą zestawu, który ma zostać zainstalowany w globalnej pamięci podręcznej zestawów.

Jeśli *gacutil.exe* nie znajduje się w ścieżce systemu, należy użyć [wiersza polecenia dewelopera *\<version>* dla programu vs ](../tools/developer-command-prompt-for-vs.md).

Poniższy przykład instaluje zestaw z nazwą pliku *hello.dll* w globalnej pamięci podręcznej zestawów.

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> We wcześniejszych wersjach .NET Framework rozszerzenie powłoki Windows *Shfusion.dll* pozwala na instalowanie zestawów przez przeciąganie ich do Eksploratora plików. Począwszy od .NET Framework 4 *Shfusion.dll* jest przestarzały.

## <a name="see-also"></a>Zobacz też

- [Pracuj z zestawami i globalną pamięcią podręczną zestawów](working-with-assemblies-and-the-gac.md)
- [Instrukcje: usuwanie zestawu z globalnej pamięci podręcznej zestawów](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (Narzędzie globalnej pamięci podręcznej zestawów)](../tools/gacutil-exe-gac-tool.md)
- [Instrukcje: podpisywanie zestawu za pomocą silnej nazwy](../../standard/assembly/sign-strong-name.md)
