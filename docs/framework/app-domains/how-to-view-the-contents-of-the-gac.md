---
title: 'Instrukcje: Wyświetlanie zawartości globalnej pamięci podręcznej zestawów'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c319c5f7c9bb808b2ce7ee10178722287e456339
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486431"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Instrukcje: Wyświetlanie zawartości globalnej pamięci podręcznej

Użyj [narzędzie global assembly cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) do wyświetlania zawartości globalnej pamięci podręcznej zestawów (GAC).

## <a name="view-the-assemblies-in-the-gac"></a>Wyświetlanie zestawów w globalnej pamięci podręcznej zestawów

Aby wyświetlić listę zestawów w globalnej pamięci podręcznej, należy otworzyć [wiersz polecenia programisty dla programu Visual Studio](../tools/developer-command-prompt-for-vs.md), a następnie wprowadź następujące polecenie:

```shell
gacutil -l
```

—lub—

```shell
gacutil /l
```

> [!NOTE]
> We wcześniejszych wersjach programu .NET Framework [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) rozszerzenie powłoki Windows umożliwia wyświetlanie globalnej pamięci podręcznej w Eksploratorze plików. Począwszy od programu .NET Framework 4, biblioteka Shfusion.dll jest przestarzała.

## <a name="see-also"></a>Zobacz także

- [Praca z zestawami i globalną pamięcią podręczną zestawów](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (narzędzie Global Assembly Cache)](../tools/gacutil-exe-gac-tool.md)
