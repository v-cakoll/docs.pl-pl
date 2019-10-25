---
title: Tworzenie nowego ASP.NET Core gRPC Project — gRPC dla deweloperów WCF
description: Dowiedz się, jak utworzyć projekt gRPC za pomocą programu Visual Studio lub z wiersza polecenia.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a30d19e1e48692ad68a648406d4bf369937744d7
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846711"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a>Tworzenie nowego projektu usługi gRPC ASP.NET Core

Platforma .NET Core udostępnia zaawansowane narzędzie interfejsu wiersza polecenia, `dotnet`, co umożliwia tworzenie projektów i rozwiązań oraz zarządzanie nimi z poziomu wiersza poleceń. Narzędzie jest ściśle zintegrowane z programem Visual Studio, więc wszystko jest również dostępne za pomocą interfejsu znanego graficznego użytkownika. W tym rozdziale przedstawiono dwa sposoby tworzenia nowego projektu ASP.NET Core gRPC: najpierw z programem Visual Studio, a następnie z interfejs wiersza polecenia platformy .NET Core.

## <a name="create-the-project-using-visual-studio"></a>Tworzenie projektu przy użyciu programu Visual Studio

> [!IMPORTANT]
> Do opracowania dowolnej aplikacji ASP.NET Core 3,0 wymagany jest program Visual Studio 2019,3 lub nowszy z zainstalowanym obciążeniem programu **ASP.NET i sieci Web** .

Utwórz puste rozwiązanie o nazwie **TraderSys** z *pustego szablonu rozwiązania* . Dodaj folder rozwiązania o nazwie `src`, a następnie kliknij prawym przyciskiem myszy folder i wybierz polecenie **dodaj** > **Nowy projekt** z menu kontekstowego. Wprowadź `grpc` w polu wyszukiwania szablonu i powinien zostać wyświetlony szablon projektu o nazwie `gRPC Service`.

![Okno dialogowe Dodawanie nowego projektu przedstawiające szablon projektu usługi gRPC Service](media/create-project/new-grpc-project.png)

Kliknij przycisk **dalej** , aby przejść do okna dialogowego **Konfigurowanie projektu** i nazwij projekt `TraderSys.Portfolios`, a następnie Dodaj `src` podkatalog do **lokalizacji**.

![Okno dialogowe Konfigurowanie projektu](media/create-project/configure-project.png)

Kliknij przycisk **dalej** , aby przejść do okna dialogowego **Nowy projekt gRPC** .

![Nowe okno dialogowe projektu gRPC](media/create-project/create-new-grpc-service.png)

Obecnie dostępne są ograniczone opcje tworzenia usługi. Platforma Docker zostanie wprowadzona w dalszej części książki, więc pozostaw pole wyboru niezaznaczone teraz, a po prostu kliknij pozycję **Utwórz**. Pierwszy ASP.NET Core 3,0 gRPC projektu jest generowany i dodawany do rozwiązania. Jeśli nie chcesz wiedzieć o pracy z `dotnet CLI`, przejdź do sekcji [czyszczenie przykładowego kodu](#clean-up-the-example-code) .

## <a name="create-the-project-using-the-net-core-cli"></a>Tworzenie projektu przy użyciu interfejs wiersza polecenia platformy .NET Core

Ta sekcja obejmuje tworzenie rozwiązań i projektów z poziomu wiersza polecenia.

Utwórz rozwiązanie, jak pokazano poniżej. Flaga `-o` (lub `--output`) określa katalog wyjściowy, który zostanie utworzony w bieżącym katalogu, jeśli nie istnieje. Rozwiązanie będzie miało taką samą nazwę jak katalog, czyli `TraderSys.sln`. Możesz podać inną nazwę przy użyciu flagi `-n` (lub `--name`).

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

ASP.NET Core 3,0 jest dostarczany z szablonem interfejsu wiersza polecenia dla usług gRPC Services. Utwórz nowy projekt przy użyciu tego szablonu, umieszczając go w podkatalogu `src` zgodnie z Konwencją dla ASP.NET Core projektów. Projekt zostanie nazwany po katalogu (tj. `TraderSys.Portfolios.csproj`), chyba że zostanie określona inna nazwa z flagą `-n`.

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

Na koniec Dodaj projekt do rozwiązania przy użyciu polecenia `dotnet sln`.

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> Ponieważ dany katalog zawiera tylko jeden plik `.csproj`, można w dalszym ciągu określić katalog, który ma zostać zapisany.

Teraz możesz otworzyć to rozwiązanie w programie Visual Studio 2019, Visual Studio Code lub dowolnym wybranym przez Ciebie edytorze.

## <a name="clean-up-the-example-code"></a>Czyszczenie przykładowego kodu

Przykładowa usługa została utworzona przy użyciu szablonu gRPC, który został wcześniej sprawdzony w książce. Nie jest to przydatne w naszym kontekście transakcji giełdowych, dlatego będziemy edytować rzeczy dla pierwszego projektu.

### <a name="rename-and-edit-the-proto-file"></a>Zmiana nazwy i edytowanie pliku proto

Przejdź dalej i Zmień nazwę pliku `Protos/greet.proto` na `Protos/portfolios.proto` i otwórz go w edytorze. Usuń wszystko po wierszu `package`, a następnie zmień nazwy `option csharp_namespace`, `package` i `service`, a następnie usuń domyślną usługę `SayHello`, aby kod wyglądał następująco.

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

W obiektach docelowych kompilacji gRPC istnieje element `Protobuf` elementu, który pozwala określić, które pliki `.proto` mają być kompilowane, i które formy generowania kodu są wymagane (czyli "serwer" lub "klient").

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a>Zmień nazwę klasy GreeterService

Klasa `GreeterService` znajduje się w folderze `Services` i dziedziczy po `Greeter.GreeterBase`. Zmień jej nazwę na `PortfolioService` i Zmień klasę bazową, aby `Portfolios.PortfoliosBase`. Usuń metody `override`.

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
