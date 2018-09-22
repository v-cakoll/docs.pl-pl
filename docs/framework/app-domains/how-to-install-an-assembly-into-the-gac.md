---
title: Instalowanie zestawu w GAC
ms.date: 09/20/2018
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
ms.openlocfilehash: d365ac77fe6cd7fc4fca36705729ec12b06d6830
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584584"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Porady: Instalowanie zestawu w globalnej pamięci podręcznej

Istnieją dwa sposoby instalacji zestawu o silnej nazwie do globalnej pamięci podręcznej zestawów (GAC).

> [!IMPORTANT]
> W pamięci podręcznej GAC można instalować tylko zestawy o silnych nazwach. Aby uzyskać informacje o sposobie tworzenia zestawu z silną nazwą, zobacz [porady: podpisywanie zestawu za pomocą silnej nazwy](how-to-sign-an-assembly-with-a-strong-name.md).

## <a name="windows-installer"></a>Instalator Windows

[Instalator Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), aparat instalacji Windows jest zalecany sposób dodawania zestawów do globalnej pamięci podręcznej. Instalator Windows zapewnia zliczanie odwołań zestawów w globalnej pamięci podręcznej i inne korzyści. Możesz użyć [zestaw narzędzi WiX rozszerzenia programu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) do utworzenia pakietu Instalatora dla Instalatora Windows.

## <a name="global-assembly-cache-tool"></a>Narzędzie Global assembly cache

Możesz użyć [narzędzie Global assembly cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) dodać zestawy o silnej nazwie do globalnej pamięci podręcznej oraz wyświetlanie zawartości globalnej pamięci podręcznej.

   > [!NOTE]
   > Narzędzie Gacutil.exe jest przeznaczone tylko do celów deweloperskich i nie powinno być używane do instalowania zestawów produkcyjnych w globalnej pamięci podręcznej zestawów.

Składnia gacutil jest następująca:

```shell
gacutil -i <assembly name>
```

W tym poleceniu *nazwy zestawu* to nazwa zestawu, aby zainstalować w globalnej pamięci podręcznej.

Poniższy przykład instaluje zestaw o nazwie pliku `hello.dll` w globalnej pamięci podręcznej.

```shell
gacutil -i hello.dll
```

> [!NOTE]
> We wcześniejszych wersjach programu .NET Framework rozszerzenie powłoki Windows Shfusion.dll umożliwia instalację zestawów przez przeciąganie ich **Eksploratora plików**. Począwszy od programu .NET Framework 4, biblioteka Shfusion.dll jest przestarzała.

## <a name="see-also"></a>Zobacz także

- [Praca z zestawami i globalną pamięcią podręczną zestawów](working-with-assemblies-and-the-gac.md)
- [Instrukcje: usuwanie zestawu z pamięci Global Assembly Cache](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (narzędzie Global Assembly Cache)](../tools/gacutil-exe-gac-tool.md)
- [Instrukcje: podpisywanie zestawu silną nazwą](how-to-sign-an-assembly-with-a-strong-name.md)