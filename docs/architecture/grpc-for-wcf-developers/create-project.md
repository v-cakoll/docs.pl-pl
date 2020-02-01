---
title: Tworzenie nowego ASP.NET Core gRPC Project — gRPC dla deweloperów WCF
description: Dowiedz się, jak utworzyć projekt gRPC za pomocą programu Visual Studio lub wiersza polecenia.
ms.date: 09/02/2019
ms.openlocfilehash: fbcc598cf503a5baeca941803ff8fa0d5fc99671
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76919414"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a>Tworzenie nowego projektu usługi gRPC ASP.NET Core

Zestaw .NET Core SDK udostępnia zaawansowane narzędzie interfejsu wiersza polecenia, `dotnet`, które umożliwia tworzenie projektów i rozwiązań oraz zarządzanie nimi z poziomu wiersza poleceń. Zestaw SDK jest ściśle zintegrowany z programem Visual Studio, więc wszystko jest również dostępne za pomocą znanego graficznego interfejsu użytkownika. W tym rozdziale przedstawiono obie metody tworzenia nowego projektu ASP.NET Core gRPC.

## <a name="create-the-project-by-using-visual-studio"></a>Tworzenie projektu przy użyciu programu Visual Studio

> [!IMPORTANT]
> Do opracowania dowolnej aplikacji ASP.NET Core 3,0 wymagany jest program Visual Studio 2019 w wersji 16,3 lub nowszej z zainstalowanym obciążeniem **programowanie ASP.NET i sieci Web** .

Utwórz puste rozwiązanie o nazwie **TraderSys** z *pustego szablonu rozwiązania* . Dodaj folder rozwiązania o nazwie `src`. Następnie kliknij prawym przyciskiem myszy folder, a następnie wybierz polecenie **dodaj** > **Nowy projekt**. Wprowadź `grpc` w polu wyszukiwania szablonu i powinien zostać wyświetlony szablon projektu o nazwie `gRPC Service`.

![Zrzut ekranu przedstawiający okno dialogowe Dodawanie nowego projektu](media/create-project/new-grpc-project.png)

Wybierz pozycję **dalej** , aby przejść do okna dialogowego **Konfigurowanie nowego projektu** . Nadaj projektowi nazwę `TraderSys.Portfolios` i Dodaj `src` podkatalogu do **lokalizacji**.

![Zrzut ekranu przedstawiający okno dialogowe Konfigurowanie nowego projektu](media/create-project/configure-project.png)

Wybierz pozycję **dalej** , aby przejść do okna dialogowego **Tworzenie nowej usługi gRPC** .

![Zrzut ekranu przedstawiający okno dialogowe Tworzenie nowej usługi gRPC](media/create-project/create-new-grpc-service.png)

W tej chwili masz ograniczoną liczbę opcji tworzenia usługi. Platforma Docker zostanie wprowadzona później, dlatego nie należy zaznaczać tej opcji. Po prostu wybierz pozycję **Utwórz**. Pierwszy ASP.NET Core 3,0 gRPC projektu jest generowany i dodawany do rozwiązania. Jeśli nie chcesz wiedzieć o pracy z `dotnet CLI`, przejdź do sekcji [czyszczenie przykładowego kodu](#clean-up-the-example-code) .

## <a name="create-the-project-by-using-the-net-core-cli"></a>Tworzenie projektu przy użyciu interfejs wiersza polecenia platformy .NET Core

Ta sekcja obejmuje tworzenie rozwiązań i projektów z poziomu wiersza polecenia.

Utwórz rozwiązanie, jak pokazano w poniższym poleceniu. Flaga `-o` (lub `--output`) określa katalog wyjściowy, który jest tworzony w bieżącym katalogu, jeśli jeszcze nie istnieje. Rozwiązanie ma taką samą nazwę jak katalog: `TraderSys.sln`. Można podać inną nazwę przy użyciu flagi `-n` (lub `--name`).

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

ASP.NET Core 3,0 jest dostarczany z szablonem interfejsu wiersza polecenia dla usług gRPC Services. Utwórz nowy projekt przy użyciu tego szablonu, umieszczając go w podkatalogu `src`, co jest konwencjonalne dla ASP.NET Core projektów. Projekt nosi nazwę po katalogu (`TraderSys.Portfolios.csproj`), chyba że zostanie określona inna nazwa z flagą `-n`.

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

Na koniec Dodaj projekt do rozwiązania przy użyciu polecenia `dotnet sln`:

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> Ponieważ konkretny katalog zawiera tylko jeden plik `.csproj`, można określić tylko katalog, aby zapisać tekst.

Teraz możesz otworzyć to rozwiązanie w programie Visual Studio 2019, Visual Studio Code lub dowolnym wybranym przez Ciebie edytorze.

## <a name="clean-up-the-example-code"></a>Czyszczenie przykładowego kodu

Przykładowa usługa została utworzona przy użyciu szablonu gRPC, który został wcześniej sprawdzony w książce. Nie jest to przydatne w naszym kontekście transakcji giełdowych, dlatego będziemy edytować rzeczy dla pierwszego projektu.

### <a name="rename-and-edit-the-proto-file"></a>Zmiana nazwy i edytowanie pliku proto

Przejdź dalej i Zmień nazwę pliku `Protos/greet.proto` na `Protos/portfolios.proto`i otwórz go w edytorze. Usuń wszystko po wierszu `package`. Następnie zmień nazwy `option csharp_namespace`, `package` i `service` i usuń domyślną usługę `SayHello`. Kod wygląda teraz następująco:

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> Szablon nie dodaje domyślnie części przestrzeni nazw `Protos`, ale dodanie go ułatwia zachowanie klas generowanych przez gRPC i własnych klas, które są wyraźnie oddzielone w kodzie.

Jeśli zmienisz nazwę pliku `greet.proto` w zintegrowanym środowisku programistycznym (IDE), takim jak Visual Studio, odwołanie do tego pliku jest automatycznie aktualizowane w pliku `.csproj`. Jednak w innym edytorze, takim jak Visual Studio Code, odwołanie nie jest aktualizowane automatycznie, dlatego należy ręcznie edytować plik projektu.

W obiektach docelowych kompilacji gRPC istnieje element elementu `Protobuf`, który pozwala określić, które pliki `.proto` mają być kompilowane, i które formy generowania kodu są wymagane (czyli "serwer" lub "klient").

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a>Zmień nazwę klasy `GreeterService`

Klasa `GreeterService` znajduje się w folderze `Services` i dziedziczy po `Greeter.GreeterBase`. Zmień nazwę na `PortfolioService`i Zmień klasę bazową, aby `Portfolios.PortfoliosBase`. Usuń metody `override`.

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

Istnieje odwołanie do klasy `GreeterService` w metodzie `Configure` w klasie `Startup`. Jeśli użyto refaktoryzacji do zmiany nazwy klasy, to odwołanie powinno zostać zaktualizowane automatycznie. Niemniej jednak, jeśli nie, musisz edytować ją ręcznie.

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

W następnej sekcji dodamy funkcjonalność do tej nowej usługi.

>[!div class="step-by-step"]
>[Poprzedni](migrate-wcf-to-grpc.md)
>[Następny](migrate-request-reply.md)
