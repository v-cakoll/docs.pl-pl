---
title: "Za pomocą generatora serializatora XML programu Microsoft .NET Core"
description: "Przegląd generatora serializatora XML firmy Microsoft."
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2017
ms.topic: tutorial
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: 4b838cafe1f4835c1c5aa6086c0997a4a9e39a9e
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/20/2018
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a>Za pomocą generatora serializatora XML programu Microsoft .NET Core

W tym samouczku jest przedstawienie sposobu Generator serializatora XML firmy Microsoft jest używany w aplikacji C# .NET Core. W trakcie tego samouczka dowiesz się:

> [!div class="checklist"]
> * Jak utworzyć aplikację .NET Core
> * Jak dodać odwołanie do pakietu Microsoft.XmlSerializer.Generator
> * Jak edytować MyApp.csproj użytkownika można dodać zależności
> * Jak dodać klasę i XmlSerializer
> * Jak skompilować i uruchomić aplikację 

Podobnie jak [Generator serializatora Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) dla programu .NET Framework [pakietu Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) jest odpowiednikiem dla projektów .NET Core i .NET Standard. Tworzy zestaw serializacji XML dla typów zawartych w zestawie poprawić wydajność uruchamiania serializacji XML podczas serializacji lub do serializacji obiektów typu przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="prerequisites"></a>Wymagania wstępne

Do ukończenia tego samouczka:

* Zainstaluj [.NET Core SDK 2.1.3 lub nowszy](https://www.microsoft.com/net/download)
* Jeśli nie jest jeszcze, należy zainstalować w edytorze kodu ulubionych.

> [!TIP]
> Należy zainstalować Edytor kodu? Spróbuj [programu Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!
  
## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a>Użyj generatora serializatora XML firmy Microsoft w aplikacji konsoli .NET Core 

Poniższe instrukcje pokazują, jak użyć generatora serializatora XML w aplikacji konsoli .NET Core.

### <a name="create-a-net-core-console-application"></a>Tworzenie aplikacji konsoli .NET Core

Otwórz wiersz polecenia i Utwórz folder o nazwie *moja_aplikacja*. Przejdź do folderu, który został utworzony i wpisz następujące polecenie:

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a>Dodaj odwołanie do pakietu Microsoft.XmlSerializer.Generator w projekcie moja_aplikacja

Użyj [ `dotnet add package` ](../tools//dotnet-add-package.md) polecenie, aby dodać odwołanie do projektu. 

Wpisz:
 
 ```console
 dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
 ```
 
### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a>Sprawdzenie zmian MyApp.csproj po dodaniu pakietu

Otwórz w edytorze kodu i do dzieła! Naszym celem jest nadal z *moja_aplikacja* budujemy aplikację w katalogu.

Otwórz *MyApp.csproj* w edytorze tekstu.

Po uruchomieniu [ `dotnet add package` ](../tools//dotnet-add-package.md) następujących wierszy polecenia, są dodawane do Twojej *MyApp.csproj* pliku projektu:

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a>Dodaj innej sekcji ItemGroup .NET Core interfejsu wiersza polecenia narzędzia pomocy technicznej
 
 Dodaj następujące wiersze po `ItemGroup` sekcji możemy inspekcji:
 
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

Dodaj następujący wiersz wewnątrz *Main* utworzyć `XmlSerializer` dla MyClass:

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a>Tworzenie i uruchamianie aplikacji

Nadal w ramach *moja_aplikacja* folderu, uruchom aplikację za pośrednictwem [ `dotnet run` ](../tools/dotnet-run.md) i automatycznie ładuje i używa serializatorów wstępnie wygenerowane w czasie wykonywania.

Wpisz następujące polecenie w oknie konsoli:

 ```console
 $ dotnet run
 ```
> [!NOTE]
> [`dotnet run`](../tools/dotnet-run.md)wywołania [ `dotnet build` ](../tools/dotnet-build.md) do upewnij się, że kompilacji są wbudowane elementy docelowe, a następnie wywołania `dotnet <assembly.dll>` do uruchomienia aplikacji docelowej.

> [!IMPORTANT]
> Polecenia i kroki opisane w tym samouczku do uruchamiania aplikacji są używane tylko w czasie tworzenia. Gdy wszystko jest gotowe do wdrożenia aplikacji, zapoznaj się z różnych [strategii wdrażania](../deploying/index.md) dla aplikacji .NET Core i [ `dotnet publish` ](../tools/dotnet-publish.md) polecenia.

Jeśli wszystko, co zakończy się powodzeniem, zestaw o nazwie *MyApp.XmlSerializers.dll* jest generowana w folderze wyjściowym. 



Gratulacje! masz tylko:
> [!div class="checklist"]
> * Utworzony .NET Core aplikacji.
> * Dodano odwołanie do pakietu Microsoft.XmlSerializer.Generator.
> * Edytować MyApp.csproj użytkownika można dodać zależności.
> * Dodaje klasę i XmlSerializer.
> * Wbudowane i uruchomienia aplikacji. 

## <a name="related-resources"></a>Powiązane zasoby

* [Wprowadzenie do serializacji XML](../../standard/serialization/introducing-xml-serialization.md)
* [Porady: serializacji przy użyciu elementu XmlSerializer (C#)](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer)
* [Porady: serializacji przy użyciu elementu XmlSerializer (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer)