---
title: 'Porady: wyświetlanie zawartości globalnej pamięci podręcznej zestawów'
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
ms.openlocfilehash: b5d8b31e7eb23789878da620f3a4517056a1ee3e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119834"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Instrukcje: wyświetlanie zawartości globalnej pamięci podręcznej zestawów

Użyj [Narzędzia globalnej pamięci podręcznej zestawów (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) , aby wyświetlić zawartość globalnej pamięci podręcznej zestawów (GAC).

## <a name="view-the-assemblies-in-the-gac"></a>Wyświetlanie zestawów w globalnej pamięci podręcznej

Aby wyświetlić listę zestawów w globalnej pamięci podręcznej zestawów, Otwórz [wiersz polecenia dla deweloperów dla programu Visual Studio](../tools/developer-command-prompt-for-vs.md), a następnie wprowadź następujące polecenie:

```shell
gacutil -l
```

— lub —

```shell
gacutil /l
```

> [!NOTE]
> We wcześniejszych wersjach .NET Framework rozszerzenie powłoki systemu Windows [Shfusion. dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) umożliwiło wyświetlanie globalnej pamięci podręcznej zestawów w Eksploratorze plików. Począwszy od .NET Framework 4 Shfusion. dll jest przestarzały.

## <a name="see-also"></a>Zobacz też

- [Praca z zestawami i globalną pamięcią podręczną zestawów](working-with-assemblies-and-the-gac.md)
- [Gacutil. exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md)
