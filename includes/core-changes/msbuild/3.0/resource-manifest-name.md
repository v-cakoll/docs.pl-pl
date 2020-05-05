---
ms.openlocfilehash: 16ee73bfc0ab33b04ea3e2fa6d0eec521a9b8634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968139"
---
### <a name="resource-manifest-file-names"></a>Nazwy plików manifestu zasobów

Począwszy od platformy .NET Core 3,0, wygenerowana nazwa pliku manifestu zasobu została zmieniona.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="change-description"></a>Zmień opis

Przed platformą .NET Core 3,0, gdy [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) metadane zostały ustawione dla pliku zasobu (*. resx*) w pliku projektu MSBuild, wygenerowana nazwa manifestu to *Namespace. ClassName. resources*. Gdy [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) nie została ustawiona, wygenerowana nazwa manifestu to *Namespace. ClassName. FolderPathRelativeToRoot. Culture. resources*.

Począwszy od platformy .NET Core 3,0, gdy plik *. resx* znajduje się w pliku źródłowym o tej samej nazwie, na przykład w aplikacjach Windows Forms, nazwa manifestu zasobu jest generowana na podstawie pełnej nazwy pierwszego typu w pliku źródłowym. Na przykład, jeśli *Type.cs* jest wspólnie z *typem Type. resx*, wygenerowana nazwa manifestu to *Namespace. ClassName. resources*. Jednak w przypadku zmodyfikowania dowolnego atrybutu `EmbeddedResource` właściwości pliku *resx* wygenerowana nazwa pliku manifestu może być różna:

- Jeśli `LogicalName` atrybut `EmbeddedResource` właściwości jest ustawiony, ta wartość jest używana jako nazwa pliku manifestu zasobu.

  Przykłady:

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  **Wygenerowana nazwa pliku manifestu zasobu**: *częśćname. resources* (niezależnie od nazwy pliku *resx* lub kultury lub innych metadanych).

- Jeśli `LogicalName` nie jest ustawiona, ale `ManifestResourceName` atrybut we `EmbeddedResource` właściwości jest ustawiony, jego wartość jest połączona z rozszerzeniem pliku *. resources*jest używana jako nazwa pliku manifestu zasobu.

  Przykłady:

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  **Wygenerowana nazwa pliku manifestu zasobu**: *częśćname. resources* lub *SomeName.fr-fr. resources*.

- Jeśli poprzednie reguły nie mają zastosowania, a `DependentUpon` atrybut w `EmbeddedResource` elemencie jest ustawiony na plik źródłowy, nazwa typu pierwszej klasy w pliku źródłowym jest używana w nazwie pliku manifestu zasobu. Dokładniej mówiąc, wygenerowana nazwa pliku to *Namespace. ClassName\[. Culture]. resources*.

  Przykłady:

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  **Wygenerowana nazwa pliku manifestu zasobu**: *Namespace. ClassName. resources* lub *Namespace.ClassName.fr-fr. resources* (gdzie `Namespace.Classname` to nazwa pierwszej klasy w *MyTypes.cs*).

- Jeśli poprzednie reguły nie mają zastosowania, `EmbeddedResourceUseDependentUponConvention` jest `true` (domyślnie dla platformy .NET Core) i istnieje plik źródłowy, który zawiera plik *. resx* o tej samej nazwie pliku podstawowego, plik *. resx* jest zależny od pasującego pliku źródłowego, a wygenerowana nazwa jest taka sama jak w poprzedniej regule. To jest reguła "ustawienia domyślne" dla projektów .NET Core.
  
  Przykłady:
  
  Pliki *MyTypes.cs* i *MyTypes.fr-fr. resx* istnieją w tym samym *folderze.*
  
  **Wygenerowana nazwa pliku manifestu zasobu**: *Namespace. ClassName. resources* lub *Namespace.ClassName.fr-fr. resources* (gdzie `Namespace.Classname` to nazwa pierwszej klasy w *MyTypes.cs*).

- Jeśli żadna z poprzednich reguł nie zostanie zastosowana, wygenerowana nazwa pliku manifestu zasobu to *RootNamespace.\[ RelativePathWithDotsForSlashes. Kultura] zasoby*. Ścieżka względna jest wartością `Link` atrybutu elementu, `EmbeddedResource` jeśli jest ustawiony. W przeciwnym razie ścieżka względna jest wartością `Identity` atrybutu `EmbeddedResource` elementu. W programie Visual Studio jest to ścieżka z katalogu głównego projektu do pliku w Eksplorator rozwiązań.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli wygenerowane nazwy manifestów nie są zadowalające, można:

- Zmodyfikuj metadane pliku zasobów zgodnie z jedną z wcześniej opisanymi regułami nazewnictwa.

- Ustaw `EmbeddedResourceUseDependentUponConvention` wartość `false` w pliku projektu, aby zrezygnować z nowej konwencji w całości:

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > Jeśli istnieją `LogicalName` atrybuty `ManifestResourceName` lub, ich wartości będą nadal używane dla wygenerowanej nazwy pliku.

#### <a name="category"></a>Kategoria

MSBuild

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak
