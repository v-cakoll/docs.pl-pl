---
title: Użyj pokrycia kodu do testów jednostkowych
description: Dowiedz się, jak korzystać z funkcji pokrycia kodu dla testów jednostkowych .NET.
author: IEvangelist
ms.author: dapine
ms.date: 06/16/2020
ms.openlocfilehash: 47f10ae367f511d5d02d32bfcb35bf4775a3e946
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990285"
---
# <a name="use-code-coverage-for-unit-testing"></a>Użyj pokrycia kodu do testów jednostkowych

Testy jednostkowe pomagają zapewnić funkcjonalność i zapewnić metodę weryfikacji w celu refaktoryzacji. Pokrycie kodu to pomiar ilości kodu, który jest uruchamiany przez testy jednostkowe — w przypadku linii, gałęzi lub metod. Przykładowo, jeśli masz prostą aplikację obejmującą tylko dwa gałęzie warunkowe kodu (_gałąź a_i _gałąź b_), test jednostkowy, który weryfikuje gałąź warunkową _,_ spowoduje zgłoszenie pokrycia kodu oddziału wynoszącego 50%.

W tym artykule omówiono użycie pokrycia kodu dla testów jednostkowych z Coverlet i generowanie raportu przy użyciu ReportGenerator. Chociaż ten artykuł koncentruje się na języku C# i xUnit jako środowisku testowym, zarówno MSTest, jak i NUnit również działają. Coverlet to [projekt typu open source w usłudze GitHub](https://github.com/coverlet-coverage/coverlet) , który zapewnia międzyplatformową strukturę pokrycia kodu dla języka C#. [Coverlet](https://dotnetfoundation.org/projects/coverlet) jest częścią .NET Foundation. Coverlet zbiera dane przebiegu testu pokrycia Cobertura, które są używane na potrzeby generowania raportów.

Ponadto w tym artykule szczegółowo przedstawiono sposób użycia informacji o pokryciu kodu zebranych z przebiegu testu Coverlet w celu wygenerowania raportu. Generowanie raportu jest możliwe przy użyciu innego [projektu Open Source w witrynie GitHub-ReportGenerator](https://github.com/danielpalme/ReportGenerator). ReportGenerator konwertuje raporty pokrycia wygenerowane przez Cobertura między wiele innych, w raportach ludzkich do odczytu w różnych formatach.

## <a name="system-under-test"></a>System w trakcie testu

"System pod testem" odnosi się do kodu, dla którego piszesz testy jednostkowe, może to być obiekt, usługa lub inne inne, które ujawniają funkcjonalność weryfikowalne. Na potrzeby tego artykułu utworzysz bibliotekę klas, która będzie testowanym systemem i dwa odpowiednie projekty testów jednostkowych.

### <a name="create-a-class-library"></a>Tworzenie biblioteki klas

W wierszu polecenia w nowym katalogu o nazwie `UnitTestingCodeCoverage` Utwórz nową bibliotekę klas .NET standard przy użyciu [`dotnet new classlib`](../tools/dotnet-new.md#classlib) polecenia:

```dotnetcli
dotnet new classlib -n Numbers
```

Poniższy fragment kodu definiuje prostą `PrimeService` klasę, która zapewnia funkcjonalność do sprawdzenia, czy jest to liczba. Skopiuj poniższy fragment kodu i Zastąp zawartość pliku *Class1.cs* , który został utworzony automatycznie w katalogu *Numbers* . Zmień nazwę pliku *Class1.cs* na *PrimeService.cs*.

```csharp
namespace System.Numbers
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            if (candidate < 2)
            {
                return false;
            }

            for (int divisor = 2; divisor <= Math.Sqrt(candidate); ++divisor)
            {
                if (candidate % divisor == 0)
                {
                    return false;
                }
            }
            return true;
        }
    }
}
```

> [!TIP]
> Warto zauważyć, że `Numbers` Biblioteka klas została celowo dodana do `System` przestrzeni nazw. Pozwala to na <xref:System.Math?displayProperty=fullName> dostęp do programu bez `using System;` deklaracji przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [przestrzeń nazw (odwołanie w C#)](../../csharp/language-reference/keywords/namespace.md).

### <a name="create-test-projects"></a>Tworzenie projektów testowych

Utwórz dwa nowe szablony **projektu testu xUnit (.NET Core)** z tego samego wiersza polecenia przy użyciu [`dotnet new xunit`](../tools/dotnet-new.md#test) polecenia:

```dotnetcli
dotnet new xunit -n XUnit.Coverlet.Collector
```

```dotnetcli
dotnet new xunit -n XUnit.Coverlet.MSBuild
```

Oba nowo utworzone projekty testowe xUnit muszą dodać odwołanie do projektu biblioteki klas *liczb* . Jest tak, aby projekty testowe miały dostęp do *PrimeService* na potrzeby testowania. W wierszu polecenia Użyj [`dotnet add`](../tools/dotnet-add-reference.md) polecenia:

```dotnetcli
dotnet add XUnit.Coverlet.Collector\XUnit.Coverlet.Collector.csproj reference Numbers\Numbers.csproj
```

```dotnetcli
dotnet add XUnit.Coverlet.MSBuild\XUnit.Coverlet.MSBuild.csproj reference Numbers\Numbers.csproj
```

Projekt programu *MSBuild* ma odpowiednie nazwy, ponieważ będzie zależeć od pakietu NuGet [coverlet. MSBuild](https://www.nuget.org/packages/coverlet.msbuild) . Dodaj tę zależność pakietu, uruchamiając [`dotnet add package`](../tools/dotnet-add-package.md) polecenie:

```dotnetcli
cd XUnit.Coverlet.MSBuild && dotnet add package coverlet.msbuild && cd ..
```

Poprzednie polecenie zmieniło katalogi skutecznie do projektu testowego *MSBuild* , a następnie dodał pakiet NuGet. Po wykonaniu tej czynności zmieniono katalogi, przechodzenie do góry o jeden poziom.

Otwórz oba pliki *UnitTest1.cs* i Zastąp ich zawartość następującym fragmentem kodu. Zmień nazwy plików *UnitTest1.cs* na *PrimeServiceTests.cs*.

```csharp
using System.Numbers;
using Xunit;

namespace XUnit.Coverlet
{
    public class PrimeServiceTests
    {
        readonly PrimeService _primeService;

        public PrimeServiceTests() => _primeService = new PrimeService();

        [
            Theory,
            InlineData(-1), InlineData(0), InlineData(1)
        ]
        public void IsPrime_ValuesLessThan2_ReturnFalse(int value) =>
            Assert.False(_primeService.IsPrime(value), $"{value} should not be prime");

        [
            Theory,
            InlineData(2), InlineData(3), InlineData(5), InlineData(7)
        ]
        public void IsPrime_PrimesLessThan10_ReturnTrue(int value) =>
            Assert.True(_primeService.IsPrime(value), $"{value} should be prime");

        [
            Theory,
            InlineData(4), InlineData(6), InlineData(8), InlineData(9)
        ]
        public void IsPrime_NonPrimesLessThan10_ReturnFalse(int value) =>
            Assert.False(_primeService.IsPrime(value), $"{value} should not be prime");
    }
}
```

### <a name="create-a-solution"></a>Tworzenie rozwiązania

W wierszu polecenia Utwórz nowe rozwiązanie, aby hermetyzować bibliotekę klas i dwa projekty testowe. Za pomocą [`dotnet sln`](../tools/dotnet-sln.md) polecenia:

```dotnetcli
dotnet new sln -n XUnit.Coverage
```

Spowoduje to utworzenie nowej nazwy pliku rozwiązania `XUnit.Coverage` w katalogu *UnitTestingCodeCoverage* . Dodaj projekty do katalogu głównego rozwiązania.

## <a name="linux"></a>[Linux](#tab/linux)

```dotnetcli
dotnet sln XUnit.Coverage.sln add **/*.csproj --in-root
```

## <a name="windows"></a>[Windows](#tab/windows)

```dotnetcli
dotnet sln XUnit.Coverage.sln add (ls **/*.csproj) --in-root
```

---

Skompiluj rozwiązanie przy użyciu [`dotnet build`](../tools/dotnet-build.md) polecenia:

```dotnetcli
dotnet build
```

Jeśli kompilacja zakończyła się pomyślnie, utworzono trzy projekty, odpowiednio przywoływane projekty i pakiety, i prawidłowo Zaktualizowano kod źródłowy. Gotowe!

## <a name="tooling"></a>Narzędzia

Istnieją dwa typy narzędzi pokrycia kodu:

- **Moduły zbierające dane:** Moduły zbierające dane monitorują wykonywanie testów i zbierają informacje o przebiegach testów. Raportuje zebrane informacje w różnych formatach wyjściowych, takich jak XML i JSON. Aby uzyskać więcej informacji, zobacz [pierwszy moduł zbierający](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/datacollector.md)dane.
- **Generatory raportów:** Używaj danych zebranych z przebiegów testowych do generowania raportów, często jako stylów HTML.

W tej sekcji fokus dotyczy narzędzi modułu zbierającego dane. Aby użyć Coverlet do pokrycia kodu, istniejący projekt testu jednostkowego musi mieć odpowiednie zależności pakietów lub alternatywnie korzystać z [narzędzi globalnych platformy .NET](../tools/global-tools.md) oraz odpowiedniego pakietu NuGet [Coverlet. Console](https://www.nuget.org/packages/coverlet.console) .

## <a name="integrate-with-net-test"></a>Integracja z testem .NET

Szablon projektu testu xUnit jest już zintegrowany z [coverlet. module zbierającym](https://www.nuget.org/packages/coverlet.collector) domyślnie.
W wierszu polecenia Zmień katalogi na projekt *XUnit. Coverlet. moduł zbierający* i uruchom [`dotnet test`](../tools/dotnet-test.md) polecenie:

```dotnetcli
cd XUnit.Coverlet.Collector && dotnet test --collect:"XPlat Code Coverage"
```

> [!NOTE]
> `"XPlat Code Coverage"`Argument jest przyjazną nazwą, która odnosi się do modułów zbierających dane z Coverlet. Ta nazwa jest wymagana, ale wielkość liter nie jest uwzględniana.

W ramach `dotnet test` przebiegu, wynikowy plik *coverage.cobertura.xml* jest wyprowadzany do katalogu *TestResults* . Plik XML zawiera wyniki. Jest to opcja międzyplatformowa, która opiera się na interfejs wiersza polecenia platformy .NET Core i jest doskonale dla systemów kompilacji, w których program MSBuild nie jest dostępny.

Poniżej znajduje się przykładowy plik *coverage.cobertura.xml* .

```xml
<?xml version="1.0" encoding="utf-8"?>
<coverage line-rate="1" branch-rate="1" version="1.9" timestamp="1592248008"
          lines-covered="12" lines-valid="12" branches-covered="6" branches-valid="6">
  <sources>
    <source>C:\</source>
  </sources>
  <packages>
    <package name="Numbers" line-rate="1" branch-rate="1" complexity="6">
      <classes>
        <class name="Numbers.PrimeService" line-rate="1" branch-rate="1" complexity="6"
               filename="Numbers\PrimeService.cs">
          <methods>
            <method name="IsPrime" signature="(System.Int32)" line-rate="1"
                    branch-rate="1" complexity="6">
              <lines>
                <line number="8" hits="11" branch="False" />
                <line number="9" hits="11" branch="True" condition-coverage="100% (2/2)">
                  <conditions>
                    <condition number="7" type="jump" coverage="100%" />
                  </conditions>
                </line>
                <line number="10" hits="3" branch="False" />
                <line number="11" hits="3" branch="False" />
                <line number="14" hits="22" branch="True" condition-coverage="100% (2/2)">
                  <conditions>
                    <condition number="57" type="jump" coverage="100%" />
                  </conditions>
                </line>
                <line number="15" hits="7" branch="False" />
                <line number="16" hits="7" branch="True" condition-coverage="100% (2/2)">
                  <conditions>
                    <condition number="27" type="jump" coverage="100%" />
                  </conditions>
                </line>
                <line number="17" hits="4" branch="False" />
                <line number="18" hits="4" branch="False" />
                <line number="20" hits="3" branch="False" />
                <line number="21" hits="4" branch="False" />
                <line number="23" hits="11" branch="False" />
              </lines>
            </method>
          </methods>
          <lines>
            <line number="8" hits="11" branch="False" />
            <line number="9" hits="11" branch="True" condition-coverage="100% (2/2)">
              <conditions>
                <condition number="7" type="jump" coverage="100%" />
              </conditions>
            </line>
            <line number="10" hits="3" branch="False" />
            <line number="11" hits="3" branch="False" />
            <line number="14" hits="22" branch="True" condition-coverage="100% (2/2)">
              <conditions>
                <condition number="57" type="jump" coverage="100%" />
              </conditions>
            </line>
            <line number="15" hits="7" branch="False" />
            <line number="16" hits="7" branch="True" condition-coverage="100% (2/2)">
              <conditions>
                <condition number="27" type="jump" coverage="100%" />
              </conditions>
            </line>
            <line number="17" hits="4" branch="False" />
            <line number="18" hits="4" branch="False" />
            <line number="20" hits="3" branch="False" />
            <line number="21" hits="4" branch="False" />
            <line number="23" hits="11" branch="False" />
          </lines>
        </class>
      </classes>
    </package>
  </packages>
</coverage>
```

> [!TIP]
> Alternatywnie można użyć pakietu MSBuild, jeśli system kompilacji korzysta już z programu MSBuild. W wierszu polecenia Zmień katalogi na projekt *XUnit. Coverlet. MSBuild* i uruchom `dotnet test` polecenie:
>
> ```dotnetcli
> dotnet test --collect:"XPlat Code Coverage"
> ```
>
> Wynikowy plik *coverage.cobertura.xml* jest wyjściowy.

## <a name="generate-reports"></a>Generowanie raportów

Teraz, gdy można zbierać dane z przebiegów testów jednostkowych, można generować raporty za pomocą [ReportGenerator](https://github.com/danielpalme/ReportGenerator). Aby zainstalować pakiet NuGet [ReportGenerator](https://www.nuget.org/packages/dotnet-reportgenerator-globaltool) jako [Narzędzie globalne platformy .NET](../tools/global-tools.md), użyj [`dotnet tool install`](../tools/dotnet-tool-install.md) polecenia:

```dotnetcli
dotnet tool install -g dotnet-reportgenerator-globaltool
```

Uruchom narzędzie i podaj odpowiednie opcje, używając pliku wyjściowego *coverage.cobertura.xml* z poprzedniego przebiegu testu.

```console
reportgenerator
"-reports:Path\To\TestProject\TestResults\{guid}\coverage.cobertura.xml"
"-targetdir:coveragereport"
-reporttypes:Html
```

Po uruchomieniu tego polecenia plik HTML reprezentuje wygenerowany raport.

:::image type="content" source="media/test-report.png" lightbox="media/test-report.png" alt-text="Raport jednostkowy wygenerowany w teście":::

## <a name="see-also"></a>Zobacz też

- [Pokrycie pokrycia testów jednostkowych w programie Visual Studio](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested)
- [Repozytorium GitHub — Coverlet](https://github.com/coverlet-coverage/coverlet)
- [Repozytorium GitHub — ReportGenerator](https://github.com/danielpalme/ReportGenerator)
- [Witryna projektu ReportGenerator](https://danielpalme.github.io/ReportGenerator)
- [Interfejs wiersza polecenia platformy .NET Core polecenie testowe](../tools/dotnet-test.md)

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Najlepsze rozwiązania dotyczące testów jednostkowych](unit-testing-best-practices.md)
