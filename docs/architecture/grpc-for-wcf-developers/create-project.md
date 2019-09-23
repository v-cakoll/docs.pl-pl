---
title: Tworzenie nowego ASP.NET Core gRPC Project — gRPC dla deweloperów WCF
description: Dowiedz się, jak utworzyć projekt gRPC za pomocą programu Visual Studio lub z wiersza polecenia.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a0fcc3f9c4e32e87260a6bc79205c909ea3800e0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184569"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a>Utwórz nowy projekt ASP.NET Core gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Platforma .NET Core udostępnia zaawansowane narzędzie `dotnet`interfejsu wiersza polecenia, które umożliwia tworzenie projektów i rozwiązań oraz zarządzanie nimi z poziomu wiersza poleceń. Narzędzie jest ściśle zintegrowane z programem Visual Studio, więc wszystko jest również dostępne za pomocą interfejsu znanego graficznego użytkownika. W tym rozdziale przedstawiono dwa sposoby tworzenia nowego projektu ASP.NET Core gRPC: najpierw z programem Visual Studio, a następnie z interfejs wiersza polecenia platformy .NET Core.

## <a name="create-the-project-using-visual-studio"></a>Tworzenie projektu przy użyciu programu Visual Studio

> [!IMPORTANT]
> Do opracowania dowolnej aplikacji ASP.NET Core 3,0 wymagany jest program Visual Studio 2019,3 lub nowszy z zainstalowanym obciążeniem programu **ASP.NET i sieci Web** .

Utwórz puste rozwiązanie o nazwie **TraderSys** z *pustego szablonu rozwiązania* . Dodaj folder rozwiązania o nazwie `src`, a następnie kliknij prawym przyciskiem myszy folder i wybierz polecenie **Dodaj** > **Nowy projekt** z menu kontekstowego. Wprowadź `grpc` ciąg w polu wyszukiwania szablonu i powinien zostać wyświetlony szablon projektu o nazwie `gRPC Service`.

![Okno dialogowe Dodawanie nowego projektu przedstawiające szablon projektu usługi gRPC Service](media/create-project/new-grpc-project.png)

Kliknij przycisk **dalej** , aby przejść do okna dialogowego **Konfigurowanie projektu** i nazwij `TraderSys.Portfolios`projekt, a następnie `src` Dodaj podkatalog do **lokalizacji**.

![Okno dialogowe Konfigurowanie projektu](media/create-project/configure-project.png)

Kliknij przycisk **dalej** , aby przejść do okna dialogowego **Nowy projekt gRPC** .

![Nowe okno dialogowe projektu gRPC](media/create-project/create-new-grpc-service.png)

Obecnie dostępne są ograniczone opcje tworzenia usługi. Platforma Docker zostanie wprowadzona w dalszej części książki, więc pozostaw pole wyboru niezaznaczone teraz, a po prostu kliknij pozycję **Utwórz**. Pierwszy ASP.NET Core 3,0 gRPC projektu jest generowany i dodawany do rozwiązania. Jeśli nie chcesz wiedzieć o pracy z programem `dotnet CLI`, przejdź do sekcji [czyszczenie przykładowego kodu](#clean-up-the-example-code) .

## <a name="create-the-project-using-the-net-core-cli"></a>Tworzenie projektu przy użyciu interfejs wiersza polecenia platformy .NET Core

Ta sekcja obejmuje tworzenie rozwiązań i projektów z poziomu wiersza polecenia.

Utwórz rozwiązanie, jak pokazano poniżej. Flaga (lub `--output`) określa katalog wyjściowy, który zostanie utworzony w bieżącym katalogu, jeśli nie istnieje. `-o` Rozwiązanie będzie miało taką samą nazwę jak katalog, czyli `TraderSys.sln`. Można podać inną nazwę przy użyciu `-n` flagi (lub `--name`).

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

ASP.NET Core 3,0 jest dostarczany z szablonem interfejsu wiersza polecenia dla usług gRPC Services. Utwórz nowy projekt przy użyciu tego szablonu, umieszczając go w `src` podkatalogu zgodnie z Konwencją dla projektów ASP.NET Core. Projekt zostanie nazwany po katalogu (tj. `TraderSys.Portfolios.csproj`), chyba że zostanie określona inna nazwa `-n` z flagą.

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

Na koniec Dodaj projekt do rozwiązania przy użyciu `dotnet sln` polecenia.

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> Ponieważ dany katalog zawiera tylko jeden `.csproj` plik, można przystąpić do określenia tylko katalogu, który ma zostać zapisany.

Teraz możesz otworzyć to rozwiązanie w programie Visual Studio 2019, Visual Studio Code lub dowolnym wybranym przez Ciebie edytorze.

## <a name="clean-up-the-example-code"></a>Czyszczenie przykładowego kodu

Przykładowa usługa została utworzona przy użyciu szablonu gRPC, który został wcześniej sprawdzony w książce. Nie jest to przydatne w naszym kontekście transakcji giełdowych, dlatego będziemy edytować rzeczy dla pierwszego projektu.

### <a name="rename-and-edit-the-proto-file"></a>Zmiana nazwy i edytowanie pliku proto

Przejdź dalej i Zmień nazwę `Protos/greet.proto` pliku na `Protos/portfolios.proto` i otwórz go w edytorze. Usuń `package` wszystko po wierszu, a następnie `package` `option csharp_namespace`Zmień nazwy i `service` i Usuń usługę domyślną `SayHello` , aby kod wyglądał następująco.

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> Szablon nie dodaje `Protos` domyślnie części przestrzeni nazw, ale dodanie go ułatwia utrzymywanie klas generowanych przez gRPC i własnych klas, które są wyraźnie oddzielone w kodzie.

Jeśli zmienisz nazwę `greet.proto` pliku w zintegrowanym środowisku programistycznym (IDE), takim jak Visual Studio, odwołanie do tego pliku zostanie automatycznie zaktualizowane `.csproj` w pliku. Jednak w innym edytorze, takim jak Visual Studio Code, odwołanie nie jest aktualizowane automatycznie, dlatego należy ręcznie edytować plik projektu.

W obiektach docelowych kompilacji gRPC istnieje `Protobuf` element elementu, który pozwala określić, które `.proto` pliki powinny zostać skompilowane, i które formy generowania kodu są wymagane (czyli "serwer" lub "klient").

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a>Zmień nazwę klasy GreeterService

Klasa znajduje się `Services` w folderze i dziedziczy z `Greeter.GreeterBase`. `GreeterService` Zmień nazwę na `PortfolioService` i Zmień klasę bazową na `Portfolios.PortfoliosBase`. `override` Usuń metody.

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

Istnieje odwołanie do `GreeterService` klasy `Configure` w metodzie w `Startup` klasie. Jeśli użyto refaktoryzacji do zmiany nazwy klasy, to odwołanie powinno zostać zaktualizowane automatycznie. Niemniej jednak, jeśli nie, musisz edytować ją ręcznie.

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
