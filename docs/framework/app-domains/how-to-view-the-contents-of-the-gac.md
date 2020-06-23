---
title: 'Instrukcje: Wyświetlanie zawartości globalnej pamięci podręcznej zestawów'
description: Dowiedz się, jak wyświetlić zawartość globalnej pamięci podręcznej zestawów w programie .NET przy użyciu narzędzia globalnej pamięci podręcznej zestawów (GAC) (gacutil.exe).
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
ms.openlocfilehash: 4d775efc073f3aad745eff7a7707efdec06172c2
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104684"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Instrukcje: wyświetlanie zawartości globalnej pamięci podręcznej zestawów

Użyj [Narzędzia globalnej pamięci podręcznej zestawów (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) , aby wyświetlić zawartość globalnej pamięci podręcznej zestawów (GAC).

## <a name="view-the-assemblies-in-the-gac"></a>Wyświetlanie zestawów w globalnej pamięci podręcznej

Aby wyświetlić listę zestawów w globalnej pamięci podręcznej zestawów, Otwórz [wiersz polecenia dla deweloperów dla programu Visual Studio](../tools/developer-command-prompt-for-vs.md), a następnie wprowadź następujące polecenie:

```shell
gacutil -l
```

-lub-

```shell
gacutil /l
```

> [!NOTE]
> We wcześniejszych wersjach .NET Framework rozszerzenie powłoki systemu Windows zostało włączone [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) , aby wyświetlić globalną pamięć podręczną zestawów w Eksploratorze plików. Począwszy od .NET Framework 4 Shfusion.dll jest przestarzały.

## <a name="see-also"></a>Zobacz też

- [Praca z zestawami i globalną pamięcią podręczną zestawów](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md)
