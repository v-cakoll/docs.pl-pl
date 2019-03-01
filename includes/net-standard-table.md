| .NET Standard              | [1.0]  | [1.1]  | [1.2] | [1.3] | [1.4] | [1.5]              | [1.6]              | [2.0]               |
|----------------------------|--------|--------|-------|-------|-------|--------------------|--------------------|---------------------|
| .NET Core                  | 1.0    | 1.0    | 1.0   | 1.0   | 1.0   | 1.0                | 1.0                | 2.0                 |
| .NET Framework <sup>1</sup>| 4.5    | 4.5    | 4.5.1 | 4.6   | 4.6.1 | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup>  |
| Mono                       | 4.6    | 4.6    | 4.6   | 4.6   | 4.6   | 4.6                | 4.6                | 5.4                 |
| Xamarin.iOS                | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0               | 10.0               | 10.14               |
| Xamarin.Mac                | 3.0    | 3.0    | 3.0   | 3.0   | 3.0   | 3.0                | 3.0                | 3.8                 |
| Xamarin.Android            | 7.0    | 7.0    | 7.0   | 7.0   | 7.0   | 7.0                | 7.0                | 8.0                 |
| Platforma uniwersalna systemu Windows | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0.16299         | 10.0.16299         | 10.0.16299          |
| Unity                      | 2018.1 | 2018.1 | 2018.1| 2018.1| 2018.1| 2018.1             |  2018.1            | 2018.1              |

<sup>1 wersji wymienionych dla programu .NET Framework mają zastosowanie do zestawu .NET Core 2.0 SDK i nowsze wersje zestawu narzędzi. Starsze wersje używane innego mapowania dla platformy .NET Standard w wersji 1.5 lub nowszej. Możesz [Pobierz narzędzia dla platformy .NET Core tools for Visual Studio 2015](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md) Jeśli nie można uaktualnić do programu Visual Studio 2017.</sup>

<sup>2 wersje wymienione w tym miejscu reprezentuje reguł, które używa NuGet, aby określić, czy dany biblioteki .NET Standard, ma zastosowanie. Gdy NuGet uwzględnia platformy .NET Framework 4.6.1 jako Obsługa .NET Standard w wersji 1.5 przy użyciu wersji 2.0, istnieją pewne problemy z korzystanie z biblioteki .NET Standard, które zostały utworzone dla tych wersji z projektów programu .NET Framework 4.6.1. Dla projektów programu .NET Framework, które muszą korzystać z tych bibliotek, zaleca się uaktualnienie projektu do środowiska .NET Framework 4.7.2 lub nowszej.</sup>

- Kolumny reprezentują wersji .NET Standard. Każda komórka nagłówek jest łącze do dokumentu, który pokazuje, w których interfejsy API stało się dodane w tej wersji programu .NET Standard.
- Wiersze reprezentują różne implementacje platformy .NET.
- Numer wersji w każdej komórce wskazuje *minimalne* wersję implementacji należy, aby skierować je do tej wersji .NET Standard.
- Interaktywny spis, można zobaczyć [wersji .NET Standard](https://immo.landwerth.net/netstandard-versions/#).

[1.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.0.md
[1.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.1.md
[1.2]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.2.md
[1.3]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.3.md
[1.4]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.4.md
[1.5]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.5.md
[1.6]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.6.md
[2.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md
