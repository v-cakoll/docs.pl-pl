---
ms.openlocfilehash: f24a29a00a1bff34a452c43716d76bf72ef277b5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206210"
---
### <a name="resource-manifest-file-name-change"></a>Zmiana nazwy pliku manifestu zasobu

Począwszy od platformy .NET Core 3,0, w domyślnym przypadku MSBuild generuje inną nazwę pliku manifestu dla plików zasobów.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="change-description"></a>Zmień opis

Przed platformą .NET Core 3,0, jeśli nie `LogicalName` , `ManifestResourceName` lub `DependentUpon` określono metadane dla `EmbeddedResource` elementu w pliku projektu, MSBuild wygenerował nazwę pliku manifestu w wzorcu `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources` . Jeśli `RootNamespace` nie jest zdefiniowana w pliku projektu, domyślnie jest to nazwa projektu. Na przykład wygenerowana nazwa manifestu dla pliku zasobów o nazwie *Form1. resx* w katalogu głównym projektu miały wartość *WebProject. Form1. resources*.

Począwszy od platformy .NET Core 3,0, jeśli plik zasobów znajduje się w pliku źródłowym o tej samej nazwie (na przykład *Form1. resx* i *Form1.cs*), MSBuild używa informacji o typie z pliku źródłowego do wygenerowania nazwy pliku manifestu w wzorcu `<Namespace>.<ClassName>.resources` . Przestrzeń nazw i nazwa klasy są wyodrębniane z pierwszego typu w umieszczonym w nim pliku źródłowym. Na przykład wygenerowana nazwa manifestu dla pliku zasobów o nazwie *Form1. resx* , który znajduje się w pliku źródłowym o nazwie *Form1.cs* , to moja *przestrzeń nazw. Form1. resources*. Kluczową kwestią jest to, że pierwsza część nazwy pliku różni się od wcześniejszych wersji platformy .NET Core (*przestrzeń nazw* , a nie *projekt*).

> [!NOTE]
> Jeśli masz `LogicalName` `ManifestResourceName` lub `DependentUpon` metadane określone dla `EmbeddedResource` elementu w pliku projektu, ta zmiana nie ma wpływu na ten plik zasobu.

Ta nieprzerwana zmiana została wprowadzona wraz z dodaniem `EmbeddedResourceUseDependentUponConvention` właściwości do projektów .NET Core. Domyślnie pliki zasobów nie są jawnie wymienione w pliku projektu .NET Core, dlatego nie zawierają `DependentUpon` metadanych, aby określić, jak należy nazwać wygenerowany plik *resources* . Gdy `EmbeddedResourceUseDependentUponConvention` jest ustawiona na `true` , jest to wartość domyślna, program MSBuild szuka współdostępnego pliku źródłowego i wyodrębni przestrzeń nazw i nazwę klasy z tego pliku. Jeśli ustawisz `EmbeddedResourceUseDependentUponConvention` `false` opcję, MSBuild generuje nazwę manifestu zgodnie z poprzednim zachowaniem, które łączy `RootNamespace` i względną ścieżkę pliku.

#### <a name="recommended-action"></a>Zalecana akcja

W większości przypadków żadna akcja nie jest wymagana w ramach dewelopera, a aplikacja powinna nadal pracować. Jeśli jednak ta zmiana spowoduje przerwanie aplikacji, można:

- Zmień kod, aby oczekiwać nowej nazwy manifestu.

- Zrezygnuj z nowej konwencji nazewnictwa, ustawiając wartość `EmbeddedResourceUseDependentUponConvention` `false` w pliku projektu.

  ```xml
  <PropertyGroup>
    <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
  </PropertyGroup>
  ```

#### <a name="category"></a>Kategoria

MSBuild

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak
