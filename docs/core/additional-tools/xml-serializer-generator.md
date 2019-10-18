---
title: Generator serializatorów XML firmy Microsoft
description: Omówienie generatora serializatorów XML firmy Microsoft. Użyj generatora serializatorów XML, aby wygenerować zestaw serializacji XML dla typów zawartych w projekcie.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 403651978667c8cf531c3f87f1156f67206fb490
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522816"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a>Używanie generatora serializatorów Microsoft XML na platformie .NET Core

W tym samouczku przedstawiono sposób użycia generatora serializatorów XML firmy Microsoft w C# aplikacji .NET Core. W ramach tego samouczka nauczysz się:

> [!div class="checklist"]
>
> - Jak utworzyć aplikację platformy .NET Core
> - Jak dodać odwołanie do pakietu Microsoft. XmlSerializer. Generator
> - Jak edytować MojaApl. csproj, aby dodać zależności
> - Jak dodać klasę i element XmlSerializer
> - Jak skompilować i uruchomić aplikację

Podobnie jak w przypadku .NET Framework [Generator serializatorów XML (Sgen. exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) , [pakiet NuGet Microsoft. XmlSerializer. Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) jest odpowiednikiem projektów .NET Core i .NET Standard. Tworzy zestaw serializacji XML dla typów zawartych w zestawie, aby zwiększyć wydajność podczas uruchamiania serializacji XML podczas serializacji lub deserializacji obiektów tych typów przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten samouczek:

- [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) lub nowszy.
- Twój ulubiony Edytor kodu.

> [!TIP]
> Musisz zainstalować Edytor kodu? Wypróbuj [program Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a>Używanie generatora serializatorów Microsoft XML w aplikacji konsolowej platformy .NET Core

Poniższe instrukcje pokazują, jak używać generatora serializatorów XML w aplikacji konsolowej programu .NET Core.

### <a name="create-a-net-core-console-application"></a>Tworzenie aplikacji konsolowej platformy .NET Core

Otwórz wiersz polecenia i Utwórz folder o nazwie *MojaApl*. Przejdź do utworzonego folderu i wpisz następujące polecenie:

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a>Dodawanie odwołania do pakietu Microsoft. XmlSerializer. Generator w projekcie MojaApl

Użyj [`dotnet add package`](../tools//dotnet-add-package.md) polecenie, aby dodać odwołanie w projekcie.

Wpisz:

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a>Sprawdź zmiany w programie MojaApl. csproj po dodaniu pakietu

Otwórz Edytor kodu i zacznijmy pracę! Nadal pracujemy nad katalogiem *MojaApl* , w którym została skompilowana aplikacja.

Otwórz w edytorze tekstów *MojaApl. csproj* .

Po uruchomieniu polecenia [`dotnet add package`](../tools//dotnet-add-package.md) do pliku projektu *MojaApl. csproj* są dodawane następujące wiersze:

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a>Dodaj kolejną sekcję elementu Item dla interfejs wiersza polecenia platformy .NET Core pomocy technicznej narzędzi

Dodaj następujące wiersze po sekcji `ItemGroup`, którą sprawdzisz:

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

### <a name="create-an-xmlserializer-for-myclass"></a>Utwórz `XmlSerializer` dla MyClass

Dodaj następujący wiersz w obszarze *głównym* , aby utworzyć `XmlSerializer` dla elementu MyClass:

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a>Kompilowanie i uruchamianie aplikacji

W folderze *MojaApl* należy uruchomić aplikację za pośrednictwem [`dotnet run`](../tools/dotnet-run.md) i automatycznie załadować i użyć wstępnie wygenerowanych serializatorów w czasie wykonywania.

W oknie konsoli wpisz następujące polecenie:

```dotnetcli
dotnet run
```

> [!NOTE]
> [`dotnet run`](../tools/dotnet-run.md) wywołań [`dotnet build`](../tools/dotnet-build.md) , aby upewnić się, że cele kompilacji zostały skompilowane, a następnie wywoła `dotnet <assembly.dll>`, aby uruchomić aplikację docelową.

> [!IMPORTANT]
> Polecenia i kroki przedstawione w tym samouczku do uruchamiania aplikacji są używane tylko w czasie projektowania. Gdy wszystko będzie gotowe do wdrożenia aplikacji, zapoznaj się z różnymi [strategiami wdrażania](../deploying/index.md) aplikacji .NET Core i poleceniem [`dotnet publish`](../tools/dotnet-publish.md) .

Jeśli wszystko powiedzie się, zestaw o nazwie *MojaApl. XmlSerializers. dll* jest generowany w folderze wyjściowym.

Nabycia! Masz właśnie:
> [!div class="checklist"]
>
> - Utworzono aplikację platformy .NET Core.
> - Dodano odwołanie do pakietu Microsoft. XmlSerializer. Generator.
> - Edycja programu MojaApl. csproj w celu dodania zależności.
> - Dodano klasę i element XmlSerializer.
> - Aplikacja została skompilowana i uruchomiona.

## <a name="related-resources"></a>Powiązane zasoby

- [Wprowadzenie do serializacji XML](../../standard/serialization/introducing-xml-serialization.md)
- [Instrukcje: Serializowanie przy użyciu elementu XmlSerializerC#()](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
- [Instrukcje: Serializowanie przy użyciu elementu XmlSerializer (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
