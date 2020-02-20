---
ms.openlocfilehash: 276268d31670b5e7dcd0ae9c0b7a61c3c38ca663
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451898"
---
### <a name="resource-manifest-file-names"></a>Nazwy plików manifestu zasobów

Począwszy od platformy .NET Core 3,0, wygenerowana nazwa pliku manifestu zasobu została zmieniona.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="change-description"></a>Zmień opis

Przed platformą .NET Core 3,0, gdy [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) metadane zostały ustawione dla pliku zasobu ( *. resx*) w pliku projektu MSBuild, wygenerowana nazwa manifestu to *Namespace. ClassName. resources*. Gdy [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) nie została ustawiona, wygenerowana nazwa manifestu to *Namespace. ClassName. FolderPathRelativeToRoot. Culture. resources*.

Począwszy od platformy .NET Core 3,0, gdy plik *. resx* znajduje się w pliku źródłowym o tej samej nazwie, na przykład w aplikacjach Windows Forms, nazwa manifestu zasobu jest generowana na podstawie pełnej nazwy pierwszego typu w pliku źródłowym. Na przykład, jeśli *Type.cs* jest wspólnie z *typem Type. resx*, wygenerowana nazwa manifestu to *Namespace. ClassName. resources*. Jednak w przypadku zmodyfikowania dowolnego atrybutu właściwości `EmbeddedResource` pliku *resx* wygenerowana nazwa pliku manifestu może być różna:

- Jeśli atrybut `LogicalName` właściwości `EmbeddedResource` jest ustawiony, ta wartość jest używana jako nazwa pliku manifestu zasobu.

  Przykłady:

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  **Wygenerowana nazwa pliku manifestu zasobu**: *częśćname. resources* (niezależnie od nazwy pliku *resx* lub kultury lub innych metadanych).

- Jeśli `LogicalName` nie jest ustawiona, ale atrybut `ManifestResourceName` właściwości `EmbeddedResource` jest ustawiony, jego wartość, łącznie z rozszerzeniem pliku *. resources*, jest używana jako nazwa pliku manifestu zasobu.

  Przykłady:

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  **Wygenerowana nazwa pliku manifestu zasobu**: *częśćname. resources* lub *SomeName.fr-fr. resources*.

- Jeśli poprzednie reguły nie mają zastosowania, a atrybut `DependentUpon` w elemencie `EmbeddedResource` jest ustawiony na plik źródłowy, nazwa typu pierwszej klasy w pliku źródłowym zostanie użyta w nazwie pliku manifestu zasobu. Dokładniej mówiąc, wygenerowana nazwa pliku to *Namespace. Classname\[. Culture]. resources*.

  Przykłady:

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  **Wygenerowana nazwa pliku manifestu zasobu**: *Namespace. ClassName. resources* lub *Namespace.ClassName.fr-fr. resources* (gdzie `Namespace.Classname` jest nazwą pierwszej klasy w *MyTypes.cs*).

- Jeśli poprzednie reguły nie mają zastosowania, `EmbeddedResourceUseDependentUponConvention` jest `true` (domyślnie w przypadku platformy .NET Core) i istnieje plik źródłowy współpracujący z plikiem *resx* , który ma taką samą nazwę pliku podstawowego, plik *. resx* jest uzależniony od pasującego pliku źródłowego, a wygenerowana nazwa jest taka sama jak w poprzedniej regule. To jest reguła "ustawienia domyślne" dla projektów .NET Core.
  
  Przykłady:
  
  Pliki *MyTypes.cs* i *MyTypes.fr-fr. resx* istnieją w tym samym *folderze.*
  
  **Wygenerowana nazwa pliku manifestu zasobu**: *Namespace. ClassName. resources* lub *Namespace.ClassName.fr-fr. resources* (gdzie `Namespace.Classname` jest nazwą pierwszej klasy w *MyTypes.cs*).
    
- Jeśli żadna z poprzednich reguł nie zostanie zastosowana, wygenerowana nazwa pliku manifestu zasobu to *RootNamespace. RelativePathWithDotsForSlashes.\[Culture.] zasoby*. Ścieżka względna jest wartością atrybutu `Link` elementu `EmbeddedResource`, jeśli jest ustawiony. W przeciwnym razie ścieżka względna jest wartością atrybutu `Identity` elementu `EmbeddedResource`. W programie Visual Studio jest to ścieżka z katalogu głównego projektu do pliku w Eksplorator rozwiązań.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli wygenerowane nazwy manifestów nie są zadowalające, można:

- Zmodyfikuj metadane pliku zasobów zgodnie z jedną z wcześniej opisanymi regułami nazewnictwa.

- Ustaw `EmbeddedResourceUseDependentUponConvention` na `false` w pliku projektu, aby zrezygnować z nowej konwencji w całości:

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > Jeśli atrybuty `LogicalName` lub `ManifestResourceName` są obecne, ich wartości będą nadal używane dla wygenerowanej nazwy pliku.

#### <a name="category"></a>Kategoria

MSBuild

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Nie dotyczy
