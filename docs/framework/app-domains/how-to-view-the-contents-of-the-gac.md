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
ms.openlocfilehash: 0375c835dea8984db34d3d1e24b2876fb9af8337
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705600"
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
> We wcześniejszych wersjach programu .NET Framework [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) rozszerzenie powłoki Windows umożliwia wyświetlanie globalnej pamięci podręcznej w Eksploratorze plików. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], biblioteka Shfusion.dll jest przestarzała.

## <a name="see-also"></a>Zobacz także

- [Praca z zestawami i globalną pamięcią podręczną zestawów](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (narzędzie Global Assembly Cache)](../tools/gacutil-exe-gac-tool.md)