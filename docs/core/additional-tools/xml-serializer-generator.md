---
title: Generator serializatora XML firmy Microsoft
description: Przegląd Generator serializatora XML firmy Microsoft. Użyj Generator serializatora XML, aby wygenerować zestawu serializacji XML dla typów zawartych w projekcie.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 74d10b0fb27a4acf477fc66451a5cf6fc1f4317c
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631693"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a>Za pomocą Generator serializatora XML firmy Microsoft na platformie .NET Core

W tym samouczku pokazano sposób użycia Generator serializatora XML firmy Microsoft w C# aplikacji .NET Core. W trakcie tego samouczka dowiesz się:

> [!div class="checklist"]
> * Jak utworzyć aplikację platformy .NET Core
> * Jak dodać odwołanie do pakietu Microsoft.XmlSerializer.Generator
> * Jak edytować swoje MyApp.csproj, aby dodać zależności
> * Jak dodać klasę i element XmlSerializer
> * Jak utworzyć i uruchomić aplikację

Podobnie jak [Generator serializatora Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) dla programu .NET Framework [pakietu Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) jest odpowiednikiem dla projektów .NET Core i .NET Standard. Tworzy zestaw serializacji XML dla typów, które są zawarte w zestawie, aby zwiększyć wydajność uruchamiania serializacji XML podczas serializacji lub deserializacji obiekty, które z tych typów, przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="prerequisites"></a>Wymagania wstępne

Do ukończenia tego samouczka:

* [Zestaw SDK programu .NET core 2.1](https://www.microsoft.com/net/download) lub nowszej
* Wybrany edytor kodu.

> [!TIP]
> Należy zainstalować Edytor kodu? Spróbuj [programu Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a>Generator serializatora XML firmy Microsoft jest używany w aplikacji konsoli .NET Core

Następujące instrukcje pokazują, jak użyć Generator serializatora XML w aplikacji konsolowej .NET Core.

### <a name="create-a-net-core-console-application"></a>Tworzenie aplikacji konsolowej .NET Core

Otwórz wiersz polecenia i Utwórz folder o nazwie *MyApp*. Przejdź do folderu, który został utworzony, a następnie wpisz następujące polecenie:

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a>Dodaj odwołanie do pakietu Microsoft.XmlSerializer.Generator w projekcie moja_aplikacja

Użyj [ `dotnet add package` ](../tools//dotnet-add-package.md) polecenie, aby dodać odwołanie w projekcie.

Wpisz:

```console
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a>Sprawdź zmiany MyApp.csproj po dodaniu pakietu

Otwieranie Edytora kodu i zaczynajmy! Wciąż pracujemy z *MyApp* utworzyliśmy aplikację w katalogu.

Otwórz *MyApp.csproj* w edytorze tekstu.

Po uruchomieniu [ `dotnet add package` ](../tools//dotnet-add-package.md) polecenia, następujące wiersze są dodawane do Twojego *MyApp.csproj* pliku projektu:

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a>Dodawanie innej sekcji ItemGroup obsługę narzędzia interfejsu wiersza polecenia programu .NET Core

Dodaj następujące wiersze po `ItemGroup` sekcji, którą firma Microsoft inspekcji:

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a>Dodaj klasę w aplikacji

Otwórz *Program.cs* w edytorze tekstu. Dodaj klasę o nazwie *MyClass* w *Program.cs*.

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a>Utwórz `XmlSerializer` dla MyClass

Dodaj następujący wiersz *Main* utworzyć `XmlSerializer` dla MyClass:

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a>Kompilowanie i uruchamianie aplikacji

Nadal w elemencie *MyApp* folder, uruchom aplikację za pośrednictwem [ `dotnet run` ](../tools/dotnet-run.md) i automatycznie ładuje i używa wstępnie wygenerowanego serializatory w środowisku uruchomieniowym.

W oknie konsoli, należy wpisać następujące polecenie:

```console
dotnet run
```

> [!NOTE]
> [`dotnet run`](../tools/dotnet-run.md) wywołania [ `dotnet build` ](../tools/dotnet-build.md) do upewnij się, że kompilacji, utworzone elementy docelowe, a następnie wywołania `dotnet <assembly.dll>` do uruchamiania aplikacji docelowej.

> [!IMPORTANT]
> Polecenia i kroki opisane w tym samouczku do uruchamiania aplikacji są używane tylko w czasie projektowania. Gdy wszystko będzie gotowe do wdrożenia aplikacji, zapoznaj się z różnych [strategie wdrażania](../deploying/index.md) dla aplikacji platformy .NET Core i [ `dotnet publish` ](../tools/dotnet-publish.md) polecenia.

Jeśli wszystko, co zakończy się powodzeniem, zestaw o nazwie *MyApp.XmlSerializers.dll* jest generowany w folderze wyjściowym.

Gratulacje! masz tylko:
> [!div class="checklist"]
> * Utworzone .NET Core aplikacji.
> * Dodano odwołanie do pakietu Microsoft.XmlSerializer.Generator.
> * Edytować swoje MyApp.csproj, aby dodać zależności.
> * Dodaje klasę i element XmlSerializer.
> * Wbudowane i uruchomienia aplikacji.

## <a name="related-resources"></a>Powiązane zasoby

* [Wprowadzenie do serializacji XML](../../standard/serialization/introducing-xml-serialization.md)
* [Instrukcje: Serializowanie przy użyciu elementu XmlSerializer (C#)](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
* [Instrukcje: Serializowanie przy użyciu elementu XmlSerializer (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
