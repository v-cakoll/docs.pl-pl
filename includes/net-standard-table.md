---
ms.openlocfilehash: 9e95db8a1530fabd30b5344c87728b9210c0ad69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74802835"
---
| .NET Standard              | [1.0]  | [1.1]  | [1.2] | [1.3] | [1.4] | [1.5]              | [1.6]              | [2.0]               | [2.1] |
|----------------------------|--------|--------|-------|-------|-------|--------------------|--------------------|---------------------|---------------------
| .NET Core                  | 1.0    | 1.0    | 1.0   | 1.0   | 1.0   | 1.0                | 1.0                | 2.0                 | 3.0 |
| Platforma .NET <sup>1</sup>| 4.5    | 4.5    | 4.5.1 | 4.6   | 4.6.1 | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup>  | Nie/A<sup>3</sup> |
| Mono                       | 4.6    | 4.6    | 4.6   | 4.6   | 4.6   | 4.6                | 4.6                | 5.4                 | 6.4 |
| Xamarin.iOS                | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0               | 10.0               | 10.14               | 12.16 |
| Xamarin.Mac                | 3.0    | 3.0    | 3.0   | 3.0   | 3.0   | 3.0                | 3.0                | 3.8                 | 5.16 |
| Xamarin.Android            | 7.0    | 7.0    | 7.0   | 7.0   | 7.0   | 7.0                | 7.0                | 8.0                 | 10.0 |
| Platforma uniwersalna systemu Windows | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0.16299         | 10.0.16299         | 10.0.16299          | TBD |
| Unity                      | 2018.1 | 2018.1 | 2018.1| 2018.1| 2018.1| 2018.1             |  2018.1            | 2018.1              | TBD |

<sup>1 Wersje wymienione dla .NET Framework mają zastosowanie do zestawu SDK .NET Core 2.0 i nowszych wersji narzędzi. Starsze wersje używane innego mapowania dla .NET Standard 1.5 i nowsze. Narzędzia [dla narzędzi .NET Core dla programu Visual Studio 2015](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md) można pobrać, jeśli nie można uaktualnić do programu Visual Studio 2017 lub nowszej wersji.</sup>

<sup>2 Wersje wymienione w tym miejscu reprezentują reguły, które NuGet używa do określenia, czy dana biblioteka .NET Standard ma zastosowanie. Podczas gdy NuGet uważa .NET Framework 4.6.1 jako obsługę .NET Standard 1.5 do 2.0, istnieje kilka problemów z korzystaniem .NET standard biblioteki, które zostały zbudowane dla tych wersji z .NET Framework 4.6.1 projektów. W przypadku projektów .NET Framework, które muszą używać takich bibliotek, zaleca się uaktualnienie projektu do celu .NET Framework 4.7.2 lub nowszego.</sup>

<sup>3 .NET Framework nie obsługuje wersji .NET Standard 2.1 lub nowszych. Aby uzyskać więcej informacji, zobacz [ogłoszenie .NET Standard 2.1](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-1/).</sup>

- Kolumny reprezentują wersje .NET Standard. Każda komórka nagłówka jest łączem do dokumentu, który pokazuje, które interfejsy API zostały dodane w tej wersji programu .NET Standard.
- Wiersze reprezentują różne implementacje .NET.
- Numer wersji w każdej komórce wskazuje *minimalną* wersję implementacji, której potrzebujesz, aby kierować ją do wersji .NET Standard.
- Aby uzyskać tabelę interakcyjną, zobacz [.NET Standard versions](https://dotnet.microsoft.com/platform/dotnet-standard#versions).

[1.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.0.md
[1.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.1.md
[1.2]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.2.md
[1.3]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.3.md
[1.4]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.4.md
[1.5]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.5.md
[1.6]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.6.md
[2.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md
[2.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.1.md
