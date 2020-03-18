---
title: Generator serializatora XML firmy Microsoft
description: Omówienie generatora serializatora Microsoft XML. Użyj Generatora serializatora XML, aby wygenerować zestaw serializacji XML dla typów zawartych w projekcie.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 094dd1227033e167050ad73121b3005a592a0ae4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714528"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a>Używanie generatora serializatora Microsoft XML w programie .NET Core

W tym samouczku nauczy cię, jak używać generatora serializatora Microsoft XML w aplikacji C# .NET Core. W trakcie tego samouczka dowiesz się:

> [!div class="checklist"]
>
> - Jak utworzyć aplikację .NET Core
> - Jak dodać odwołanie do pakietu Microsoft.XmlSerializer.Generator
> - Jak edytować plik MyApp.csproj, aby dodać zależności
> - Jak dodać klasę i obiekt XmlSerializer
> - Jak skompilować i uruchomić aplikację

Podobnie jak [Generator serializatora Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) dla programu .NET Framework, [pakiet Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) jest odpowiednikiem projektów .NET Core i .NET Standard. Tworzy zestaw serializacji XML dla typów zawartych w zestawie, aby zwiększyć wydajność uruchamiania serializacji XML podczas <xref:System.Xml.Serialization.XmlSerializer>serializacji lub deserializacji obiektów tych typów przy użyciu .

## <a name="prerequisites"></a>Wymagania wstępne

W celu ukończenia tego samouczka:

- [SDK .NET Core 2.1](https://dotnet.microsoft.com/download) lub nowszy.
- Twój ulubiony edytor kodu.

> [!TIP]
> Chcesz zainstalować edytor kodów? [Wypróbuj program Visual Studio!](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a>Używanie generatora serializatora Microsoft XML w aplikacji konsoli .NET Core

W poniższych instrukcjach przedstawiono sposób używania generatora serializatora XML w aplikacji konsoli .NET Core.

### <a name="create-a-net-core-console-application"></a>Tworzenie aplikacji konsolowej platformy .NET Core

Otwórz wiersz polecenia i utwórz folder o nazwie *Mojaaplikacja*. Przejdź do utworzonego folderu i wpisz następujące polecenie:

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a>Dodawanie odwołania do pakietu Microsoft.XmlSerializer.Generator w projekcie MyApp

Użyj [`dotnet add package`](../tools//dotnet-add-package.md) polecenia, aby dodać odwołanie w projekcie.

Wpisz:

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a>Sprawdź zmiany w myapp.csproj po dodaniu pakietu

Otwórz edytor kodu i zacznijmy! Nadal pracujemy z katalogu *MyApp,* w który stworzyliśmy aplikację.

Otwórz *MyApp.csproj* w edytorze tekstu.

Po uruchomieniu [`dotnet add package`](../tools//dotnet-add-package.md) polecenia do pliku projektu *MyApp.csproj* są dodawane następujące wiersze:

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a>Dodawanie innej sekcji ItemGroup dla obsługi narzędzia CLI platformy .NET Core

Dodaj następujące wiersze `ItemGroup` po sekcji, którą sprawdziliśmy:

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a>Dodawanie klasy w aplikacji

Otwórz *Program.cs* w edytorze tekstu. Dodaj klasę o nazwie *MyClass* w *Program.cs*.

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a>Tworzenie `XmlSerializer` dla MyClass

Dodaj następujący wiersz wewnątrz *Main,* aby utworzyć `XmlSerializer` for MyClass:

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a>Kompilowanie i uruchamianie aplikacji

Nadal w folderze *MyApp* uruchom [`dotnet run`](../tools/dotnet-run.md) aplikację za pośrednictwem i automatycznie ładuje i używa wstępnie wygenerowanych serializatorów w czasie wykonywania.

Wpisz następujące polecenie w oknie konsoli:

```dotnetcli
dotnet run
```

> [!NOTE]
> [`dotnet run`](../tools/dotnet-run.md)wywołania, [`dotnet build`](../tools/dotnet-build.md) aby upewnić się, że obiekty `dotnet <assembly.dll>` docelowe kompilacji zostały utworzone, a następnie wywołuje do uruchomienia aplikacji docelowej.

> [!IMPORTANT]
> Polecenia i kroki przedstawione w tym samouczku do uruchamiania aplikacji są używane tylko w czasie programowania. Gdy wszystko będzie gotowe do wdrożenia aplikacji, zapoznaj się z [różnymi strategiami wdrażania](../deploying/index.md) aplikacji .NET Core i [`dotnet publish`](../tools/dotnet-publish.md) polecenia.

Jeśli wszystko się powiedzie, w folderze wyjściowym jest generowany zestaw o nazwie *MyApp.XmlSerializers.dll.*

Gratulacje! Masz tylko:
> [!div class="checklist"]
>
> - Utworzono aplikację .NET Core.
> - Dodano odwołanie do pakietu Microsoft.XmlSerializer.Generator.
> - Edytowałem urządzenie MyApp.csproj, aby dodać zależności.
> - Dodano klasę i XmlSerializer.
> - Zbudowano i uruchomiono aplikację.

## <a name="related-resources"></a>Powiązane zasoby

- [Wprowadzenie do serializacji XML](../../standard/serialization/introducing-xml-serialization.md)
- [Jak serializować za pomocą XmlSerializer (C#)](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
- [Jak: Serializuj przy użyciu XmlSerializer (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
