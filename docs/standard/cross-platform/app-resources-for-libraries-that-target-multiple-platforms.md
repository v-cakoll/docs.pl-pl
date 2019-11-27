---
title: Zasoby aplikacji dla bibliotek przeznaczonych do wielu platform
ms.date: 07/18/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multiple platforms, resources for
- resources [.NET Framework]
- .NET Framework, resources when targeting multiple platforms
- resources, for multiple platforms
- targeting multiple platforms, resources for
ms.assetid: 72c76f0b-7255-4576-9261-3587f949669c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b32c2e354ea48e25ddb0aa561eb576cbfd89e3fb
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204737"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Zasoby aplikacji dla bibliotek przeznaczonych do wielu platform
Można użyć typu projektu [Biblioteka klas przenośnych](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) .NET Framework, aby upewnić się, że zasoby w bibliotekach klas są dostępne z wielu platform. Ten typ projektu jest dostępny w programie Visual Studio 2012 i jest przeznaczony dla przenośnego podzestawu biblioteki klas .NET Framework. Za pomocą przenośnej biblioteki klas zapewnia dostęp do biblioteki z aplikacji klasycznych, aplikacji Silverlight, aplikacji Windows Phone i aplikacji ze sklepu Windows 8. x.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 Projekt biblioteki klas przenośnych sprawia, że tylko bardzo ograniczony podzbiór typów w przestrzeni nazw <xref:System.Resources> dostępne dla aplikacji, ale umożliwia korzystanie z klasy <xref:System.Resources.ResourceManager> do pobierania zasobów. Jeśli jednak tworzysz aplikację przy użyciu programu Visual Studio, należy użyć otoki silnie wpisanej utworzonej przez program Visual Studio, a nie bezpośrednio używać klasy <xref:System.Resources.ResourceManager>.

 Aby utworzyć silnie wpisaną otokę w programie Visual Studio, ustaw **modyfikator dostępu** głównego pliku zasobów w projektancie zasobów programu Visual Studio na **publiczny**. Spowoduje to utworzenie pliku [NazwaPlikuZasobów].designer.cs lub [NazwaPlikuZasobów].designer.vb zawierającego silnie typizowaną otokę ResourceManager. Aby uzyskać więcej informacji o używaniu otoki zasobów o jednoznacznie określonym typie, zobacz sekcję "Generowanie klasy zasobów o jednoznacznie określonym typie" w temacie [Resgen. exe (Resource File Generator)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) .

## <a name="resource-manager-in-the-portable-class-library"></a>Menedżer zasobów w bibliotece klas przenośnych
 W projekcie biblioteki klas przenośnych cały dostęp do zasobów jest obsługiwany przez klasę <xref:System.Resources.ResourceManager>. Ponieważ typy w przestrzeni nazw <xref:System.Resources>, takie jak <xref:System.Resources.ResourceReader> i <xref:System.Resources.ResourceSet>, nie są dostępne z poziomu projektu biblioteki klas przenośnych, nie mogą być używane do uzyskiwania dostępu do zasobów.

 Projekt biblioteki klas przenośnych zawiera cztery składowe <xref:System.Resources.ResourceManager> wymienione w poniższej tabeli. Te konstruktory i metody umożliwiają utworzenie wystąpienia obiektu <xref:System.Resources.ResourceManager> i pobranie zasobów ciągu.

|`ResourceManager` składową|Opis|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Tworzy wystąpienie <xref:System.Resources.ResourceManager>, aby uzyskać dostęp do nazwanego pliku zasobów znalezionego w określonym zestawie.|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Tworzy wystąpienie <xref:System.Resources.ResourceManager> odpowiadające określonemu typowi.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Pobiera nazwany zasób dla bieżącej kultury.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Pobiera nazwany zasób należący do określonej kultury.|

 Wykluczenie innych elementów członkowskich <xref:System.Resources.ResourceManager> z przenośnej biblioteki klas oznacza, że nie można pobrać z pliku zasobów obiektów serializowanych, danych niebędących ciągami ani obrazów. Aby używać zasobów z przenośnej biblioteki klas, należy przechowywać wszystkie dane obiektów w postaci ciągów. Na przykład można przechowywać wartości numeryczne w pliku zasobów, konwertując je na ciągi i można je pobrać, a następnie przekonwertować z powrotem na liczby przy użyciu metody `Parse` lub `TryParse` typu danych liczbowych. Możesz konwertować obrazy lub inne dane binarne na reprezentację ciągu, wywołując metodę <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> i przywracając je do tablicy bajtów, wywołując metodę <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType>.

## <a name="the-portable-class-library-and-windows-store-apps"></a>Przenośna biblioteka klas i aplikacje ze sklepu Windows
 Przenośne biblioteki klas są przechowywane w plikach resx, które następnie są kompilowane do plików. resources i osadzone w zestawie głównym lub w zestawach satelickich w czasie kompilacji. Z drugiej strony aplikacje ze sklepu Windows 8. x wymagają, aby zasoby były przechowywane w plikach. resw, które następnie są kompilowane w jednym pliku indeksu zasobów pakietu (PRI). Jednak pomimo niezgodnych formatów plików Biblioteka klas przenośnych będzie działała w aplikacji ze sklepu Windows 8. x.

 Aby korzystać z biblioteki klas z aplikacji ze sklepu Windows 8. x, Dodaj odwołanie do niej w projekcie aplikacji ze sklepu Windows. Program Visual Studio będzie w sposób przezroczysty wyodrębniał zasoby z zestawu do pliku. resw i użyje go do wygenerowania pliku PRI, z którego środowisko wykonawcze systemu Windows mogą wyodrębnić zasoby. W czasie wykonywania środowisko wykonawcze systemu Windows wykonuje kod w przenośnej bibliotece klas, ale pobiera zasoby biblioteki klas przenośnych z pliku PRI.

 Jeśli projekt biblioteki klas przenośnych zawiera zlokalizowane zasoby, należy użyć modelu Hub i szprych do wdrożenia ich w taki sam sposób jak w przypadku biblioteki w aplikacji klasycznej. Aby użyć głównego pliku zasobów i wszystkich zlokalizowanych plików zasobów w aplikacji ze sklepu Windows 8. x, Dodaj odwołanie do głównego zestawu. W czasie kompilacji program Visual Studio wyodrębnia zasoby z głównego pliku zasobów i plików zasobów zlokalizowanych do oddzielnych plików resw. Następnie kompiluje pliki. resw do pojedynczego pliku PRI, do którego środowisko wykonawcze systemu Windows uzyskuje dostęp w czasie wykonywania.

<a name="NonLoc"></a>
## <a name="example-non-localized-portable-class-library"></a>Przykład: Przenośna biblioteka klas niezlokalizowanych
 Poniższy prosty, Niezlokalizowany, przenośny Biblioteka klas używa zasobów do przechowywania nazw kolumn i określania liczby znaków do zarezerwowania dla danych tabelarycznych. W przykładzie do przechowywania zasobów ciągów wymienionych w poniższej tabeli użyto pliku o nazwie LibResources.resx.

|Nazwa zasobu|Wartość zasobu|
|-------------------|--------------------|
|Born|Data urodzenia|
|BornLength|12|
|Hired|Data zatrudnienia|
|HiredLength|12|
|ID|ID|
|ID.Length|12|
|Nazwa|Nazwa|
|NameLength|25|
|Tytuł|Baza danych pracowników|

 Poniższy kod definiuje klasę `UILibrary`, która używa otoki Menedżer zasobów o nazwie `resources` wygenerowanej przez program Visual Studio, gdy **modyfikator dostępu** dla pliku zostanie zmieniony na **Public**. Klasa UILibrary analizuje dane ciągu w razie potrzeby. . Należy zauważyć, że Klasa znajduje się w przestrzeni nazw `MyCompany.Employees`.

 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]

 Poniższy kod ilustruje sposób, w jaki Klasa `UILibrary` i jej zasoby są dostępne z poziomu aplikacji w trybie konsoli. Wymaga odwołania do UILibrary. dll, które ma zostać dodane do projektu aplikacji konsoli.

 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]

 Poniższy kod ilustruje sposób, w jaki Klasa `UILibrary` i jej zasoby są dostępne z poziomu aplikacji ze sklepu Windows 8. x. Wymaga odwołania do UILibrary. dll, które ma zostać dodane do projektu aplikacji ze sklepu Windows.

 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]

## <a name="example-localized-portable-class-library"></a>Przykład: zlokalizowana Biblioteka klas przenośnych
 Następujący zlokalizowany przykład biblioteki klas przenośnych zawiera zasoby dla kultur francuski (Francja) i angielskiego (Stany Zjednoczone). Kultura angielska (Stany Zjednoczone) jest kulturą domyślną aplikacji; jego zasoby są wyświetlane w tabeli w [poprzedniej sekcji](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). Plik zasobów dla kultury Francuski (Francja) o nazwie LibResources.fr-FR.resx składa się z zasobów ciągu wymienionych w poniższej tabeli. Kod źródłowy klasy `UILibrary` jest taki sam, jak pokazano w poprzedniej sekcji.

|Nazwa zasobu|Wartość zasobu|
|-------------------|--------------------|
|Born|Date de naissance|
|BornLength|20|
|Hired|Date embauché|
|HiredLength|16|
|ID|ID|
|Nazwa|Nom|
|Tytuł|Base de données des employés|

 Poniższy kod ilustruje sposób, w jaki Klasa `UILibrary` i jej zasoby są dostępne z poziomu aplikacji w trybie konsoli. Wymaga odwołania do UILibrary. dll, które ma zostać dodane do projektu aplikacji konsoli.

 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]

 Poniższy kod ilustruje sposób, w jaki Klasa `UILibrary` i jej zasoby są dostępne z poziomu aplikacji ze sklepu Windows 8. x. Wymaga odwołania do UILibrary. dll, które ma zostać dodane do projektu aplikacji ze sklepu Windows. Używa właściwości `ApplicationLanguages.PrimaryLanguageOverride` statycznej, aby ustawić preferowany język aplikacji w języku francuskim.

 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Resources.ResourceManager>
- [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)
- [Opakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
