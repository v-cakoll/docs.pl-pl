---
title: Generator serializatorów XML firmy Microsoft
description: Omówienie generatora serializatorów XML firmy Microsoft. Użyj generatora serializatorów XML, aby wygenerować zestaw serializacji XML dla typów zawartych w projekcie.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 252d5f6655336669ba516393e17eb3d070611ea6
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849234"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a>Używanie generatora serializatorów Microsoft XML na platformie .NET Core

W tym samouczku przedstawiono sposób użycia generatora serializatorów XML firmy Microsoft w C# aplikacji .NET Core. W ramach tego samouczka nauczysz się:

> [!div class="checklist"]
> * Jak utworzyć aplikację platformy .NET Core
> * Jak dodać odwołanie do pakietu Microsoft. XmlSerializer. Generator
> * Jak edytować MojaApl. csproj, aby dodać zależności
> * Jak dodać klasę i element XmlSerializer
> * Jak skompilować i uruchomić aplikację

Podobnie jak w przypadku .NET Framework [Generator serializatorów XML (Sgen. exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) , [pakiet NuGet Microsoft. XmlSerializer. Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) jest odpowiednikiem projektów .NET Core i .NET Standard. Tworzy zestaw serializacji XML dla typów zawartych w zestawie, aby zwiększyć wydajność podczas uruchamiania serializacji XML podczas serializacji lub deserializacji obiektów tych typów przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten samouczek:

* [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) lub nowszy
* Twój ulubiony Edytor kodu.

> [!TIP]
> Musisz zainstalować Edytor kodu? Wypróbuj [program Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a>Używanie generatora serializatorów Microsoft XML w aplikacji konsolowej platformy .NET Core

Poniższe instrukcje pokazują, jak używać generatora serializatorów XML w aplikacji konsolowej programu .NET Core.

### <a name="create-a-net-core-console-application"></a>Tworzenie aplikacji konsolowej platformy .NET Core

Otwórz wiersz polecenia i Utwórz folder o nazwie *MojaApl*. Przejdź do utworzonego folderu i wpisz następujące polecenie:

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a>Dodawanie odwołania do pakietu Microsoft. XmlSerializer. Generator w projekcie MojaApl

Użyj polecenia [`dotnet add package`](../tools//dotnet-add-package.md) , aby dodać odwołanie w projekcie.

Wpisz:

```console
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a>Sprawdź zmiany w programie MojaApl. csproj po dodaniu pakietu

Otwórz Edytor kodu i zacznijmy pracę! Nadal pracujemy nad katalogiem *MojaApl* , w którym została skompilowana aplikacja.

Otwórz w edytorze tekstów *MojaApl. csproj* .

Po uruchomieniu [`dotnet add package`](../tools//dotnet-add-package.md) polecenia do pliku projektu *MojaApl. csproj* są dodawane następujące wiersze:

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a>Dodaj kolejną sekcję elementu Item dla interfejs wiersza polecenia platformy .NET Core pomocy technicznej narzędzi

Dodaj następujące wiersze po `ItemGroup` sekcji, którą sprawdzisz:

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a>Dodawanie klasy w aplikacji

Otwórz *program.cs* w edytorze tekstu. Dodaj klasę o nazwie *MyClass* w *program.cs*.

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a>Utwórz dla `XmlSerializer` elementu MyClass

Dodaj następujący wiersz w obszarze *głównym* , aby utworzyć `XmlSerializer` for MyClass:

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a>Kompilowanie i uruchamianie aplikacji

Nadal w folderze *MojaApl* Uruchom aplikację za pośrednictwem [`dotnet run`](../tools/dotnet-run.md) programu, która automatycznie ładuje i używa wstępnie wygenerowanych serializatorów w czasie wykonywania.

W oknie konsoli wpisz następujące polecenie:

```console
dotnet run
```

> [!NOTE]
> [`dotnet run`](../tools/dotnet-run.md)wywołuje [`dotnet build`](../tools/dotnet-build.md) się, by upewnić się, że cele kompilacji zostały skompilowane `dotnet <assembly.dll>` , a następnie wywołuje, aby uruchomić aplikację docelową.

> [!IMPORTANT]
> Polecenia i kroki przedstawione w tym samouczku do uruchamiania aplikacji są używane tylko w czasie projektowania. Gdy wszystko będzie gotowe do wdrożenia aplikacji, zapoznaj się z różnymi [strategiami wdrażania](../deploying/index.md) aplikacji .NET Core i [`dotnet publish`](../tools/dotnet-publish.md) poleceniem.

Jeśli wszystko powiedzie się, zestaw o nazwie *MojaApl. XmlSerializers. dll* jest generowany w folderze wyjściowym.

Gratulacje! Masz właśnie:
> [!div class="checklist"]
> * Utworzono aplikację platformy .NET Core.
> * Dodano odwołanie do pakietu Microsoft. XmlSerializer. Generator.
> * Edycja programu MojaApl. csproj w celu dodania zależności.
> * Dodano klasę i element XmlSerializer.
> * Aplikacja została skompilowana i uruchomiona.

## <a name="related-resources"></a>Powiązane zasoby

* [Wprowadzenie do serializacji XML](../../standard/serialization/introducing-xml-serialization.md)
* [Instrukcje: Serializacja przy użyciu elementu XmlSerializerC#()](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
* [Instrukcje: Serializacja przy użyciu elementu XmlSerializer (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
