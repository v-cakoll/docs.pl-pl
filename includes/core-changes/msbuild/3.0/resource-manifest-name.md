---
ms.openlocfilehash: 16ee73bfc0ab33b04ea3e2fa6d0eec521a9b8634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968139"
---
### <a name="resource-manifest-file-names"></a>Nazwy plików manifestu zasobów

Począwszy od .NET Core 3.0, nazwa pliku manifestu wygenerowanego zasobu została zmieniona.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="change-description"></a>Zmień opis

Przed .NET Core 3.0, gdy w pliku projektu MSBuild ustawiono metadane [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) dla pliku zasobu *(.resx),* wygenerowaną nazwą manifestu była *namespace.Classname.resources*. Gdy nie ustawiono [dependentUpon,](/visualstudio/msbuild/common-msbuild-project-items#compile) wygenerowaną nazwą manifestu był *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.

Począwszy od .NET Core 3.0, gdy plik *.resx* jest współlokowane z plikiem źródłowym o tej samej nazwie, na przykład w aplikacjach Formularzy systemu Windows, nazwa manifestu zasobu jest generowany na podstawie pełnej nazwy pierwszego typu w pliku źródłowym. Na przykład jeśli *Type.cs* jest zlokalizowany z *Type.resx*, wygenerowana nazwa manifestu to *Namespace.Classname.resources*. Jeśli jednak zmodyfikujesz którykolwiek `EmbeddedResource` z atrybutów właściwości pliku *.resx,* wygenerowana nazwa pliku manifestu może być inna:

- Jeśli `LogicalName` atrybut we `EmbeddedResource` właściwości jest ustawiony, ta wartość jest używana jako nazwa pliku manifestu zasobu.

  Przykłady:

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  **Nazwa pliku manifestu wygenerowanego zasobu**: *SomeName.resources* (niezależnie od nazwy pliku *.resx* lub kultury lub innych metadanych).

- Jeśli `LogicalName` nie jest ustawiona, `ManifestResourceName` ale `EmbeddedResource` atrybut we właściwości jest ustawiona, jego wartość, w połączeniu z rozszerzeniem pliku *.resources*, jest używany jako nazwa pliku manifestu zasobu.

  Przykłady:

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  **Nazwa pliku manifestu wygenerowanego zasobu:** *SomeName.resources* lub *SomeName.fr-FR.resources*.

- Jeśli poprzednie reguły nie mają zastosowania, `DependentUpon` a `EmbeddedResource` atrybut elementu jest ustawiony na plik źródłowy, nazwa typu pierwszej klasy w pliku źródłowym jest używana w nazwie pliku manifestu zasobu. Dokładniej, wygenerowana nazwa pliku to *\[Namespace.Classname . Kultura].zasoby*.

  Przykłady:

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  **Nazwa pliku manifestu wygenerowanego zasobu**: *Namespace.Classname.resources* lub *Namespace.Classname.fr-FR.resources* (gdzie `Namespace.Classname` jest nazwą pierwszej klasy w *MyTypes.cs).*

- Jeśli poprzednie reguły nie mają `EmbeddedResourceUseDependentUponConvention` `true` zastosowania, jest (domyślnie dla .NET Core) i istnieje plik źródłowy colocated z plikiem *.resx,* który ma tę samą nazwę pliku podstawowego, plik *.resx* jest zależny od pasującego pliku źródłowego, a wygenerowana nazwa jest taka sama jak w poprzedniej regule. Jest to reguła "ustawień domyślnych" dla projektów .NET Core.
  
  Przykłady:
  
  Pliki *MyTypes.cs* i *MyTypes.resx* lub *MyTypes.fr-FR.resx* istnieją w tym samym folderze.
  
  **Nazwa pliku manifestu wygenerowanego zasobu**: *Namespace.Classname.resources* lub *Namespace.Classname.fr-FR.resources* (gdzie `Namespace.Classname` jest nazwą pierwszej klasy w *MyTypes.cs).*

- Jeśli żadna z poprzednich reguł nie ma zastosowania, wygenerowaną nazwą pliku manifestu zasobu jest *RootNamespace.RelativePathWithDotsForSlashes.\[ Kultura.] zasobów*. Ścieżka względna jest `Link` wartością `EmbeddedResource` atrybutu elementu, jeśli jest ustawiona. W przeciwnym razie ścieżka względna jest wartością `Identity` atrybutu `EmbeddedResource` elementu. W programie Visual Studio jest to ścieżka od katalogu głównego projektu do pliku w Eksploratorze rozwiązań.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli nie jesteś zadowolony z wygenerowanych nazw manifestów, możesz:

- Zmodyfikuj metadane pliku zasobów zgodnie z jedną z wcześniej opisanych reguł nazewnictwa.

- Ustaw `EmbeddedResourceUseDependentUponConvention` `false` w pliku projektu, aby całkowicie zrezygnować z nowej konwencji:

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > Jeśli `LogicalName` lub `ManifestResourceName` atrybuty są obecne, ich wartości będą nadal używane dla wygenerowanej nazwy pliku.

#### <a name="category"></a>Kategoria

MSBuild

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Nie dotyczy
