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
ms.openlocfilehash: a6c589a393ccfb5610a19776af6e33e4046bf5d3
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2018
ms.locfileid: "46711314"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Zasoby aplikacji dla bibliotek przeznaczonych do wielu platform
Można użyć programu .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) projektu typu, aby upewnić się, że zasoby w bibliotekach klas są dostępne na wielu platformach. Ten typ projektu jest dostępna w [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] i jest przeznaczony dla przenośny podzestaw biblioteki klas .NET Framework. Za pomocą [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] gwarantuje, że biblioteki są dostępne z aplikacji komputerowych, aplikacji Silverlight, aplikacji Windows Phone i [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.  

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]
  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] Projektu sprawia, że tylko bardzo ograniczony podzestaw typów z <xref:System.Resources> przestrzeni nazw jest dostępna dla aplikacji, ale umożliwiają używanie <xref:System.Resources.ResourceManager> klasy w celu pobierania zasobów. Jednak jeśli tworzysz aplikację za pomocą programu Visual Studio, należy używać silnie typizowaną otokę utworzone przez program Visual Studio zamiast używania <xref:System.Resources.ResourceManager> klasy bezpośrednio.  
  
 Aby utworzyć silnie typizowaną otokę w programie Visual Studio, należy ustawić głównego pliku zasobów **modyfikator dostępu** w Projektancie zasobów Visual Studio, aby **publicznych**. Spowoduje to utworzenie pliku [NazwaPlikuZasobów].designer.cs lub [NazwaPlikuZasobów].designer.vb zawierającego silnie typizowaną otokę ResourceManager. Aby uzyskać więcej informacji o korzystaniu z silnie typizowanej otoki zasobów, zobacz sekcję "Generowanie silnie Typizowanej klasy zasobów" w [Resgen.exe (Generator pliku zasobów)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) tematu.  
  
## <a name="resource-manager-in-the-includenetportableincludesnet-portable-mdmd"></a>Menedżer zasobów w [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 W [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, dostęp do zasobów jest obsługiwane przez <xref:System.Resources.ResourceManager> klasy. Ponieważ typy w <xref:System.Resources> przestrzeni nazw, takich jak <xref:System.Resources.ResourceReader> i <xref:System.Resources.ResourceSet>, nie są dostępne z [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, nie można uzyskać dostęp do zasobów.  
  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] Projektu obejmuje cztery <xref:System.Resources.ResourceManager> elementy członkowskie wymienione w poniższej tabeli. Te konstruktory i metody umożliwiają utworzenia wystąpienia <xref:System.Resources.ResourceManager> obiektu i pobranie zasobów ciągu.  
  
|`ResourceManager` Element członkowski|Opis|  
|------------------------------|-----------------|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Tworzy <xref:System.Resources.ResourceManager> wystąpienie do dostępu do nazwanego pliku zasobów w określonym zestawie.|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Tworzy <xref:System.Resources.ResourceManager> wystąpienia, która odnosi się do określonego typu.|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Pobiera nazwany zasób dla bieżącej kultury.|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Pobiera nazwany zasób należący do określonej kultury.|  
  
 Wykluczenie innych <xref:System.Resources.ResourceManager> członków z [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] oznacza, że serializacji obiektów, danych innych niż ciąg oraz obrazów nie można pobrać z pliku zasobów. Aby używać zasobów z [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], wszystkie dane obiektów należy przechowywać w postaci ciągu. Na przykład, można przechowywać wartości liczbowe w pliku zasobów po przekonwertowaniu ich na ciągi znaków i można je pobrać i następnie przekonwertować z powrotem na liczby przy użyciu typu danych liczbowych `Parse` lub `TryParse` metody. Na reprezentację ciągu można przekonwertować obrazy lub inne dane binarne, wywołując <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> metoda i przywracania ich do typu byte array, wywołując <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType> metody.  
  
## <a name="the-includenetportableincludesnet-portable-mdmd-and-windows-store-apps"></a>[!INCLUDE[net_portable](../../../includes/net-portable-md.md)] i aplikacje Windows Store  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projekty przechowują zasoby w plikach resx, które są następnie kompilowane do plików Resources i osadzone w głównym zestawie lub zestawach satelickich w czasie kompilacji. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacje, z drugiej strony, wymagają zasoby, które mają być przechowywane w plikach resw, które są następnie kompilowane do plik indeksu (PRI) zasobów w jednym pakiecie. Jednak mimo niezgodnych formatów pliku Twoje [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] będzie działać w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.  
  
 Aby skorzystać z biblioteki klas z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, Dodaj odwołanie do niej w projekcie aplikacji Windows Store. Visual Studio sposób niewidoczny wyodrębniać zasoby z zestawu do pliku resw i go użyć do wygenerowania pliku PRI, z którego [!INCLUDE[wrt](../../../includes/wrt-md.md)] może wyodrębnić zasoby. W czasie wykonywania [!INCLUDE[wrt](../../../includes/wrt-md.md)] wykonuje kod w swojej [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], ale pobiera zasoby z biblioteki klas przenośnych z pliku PRI.  
  
 Jeśli Twoje [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu zawiera zlokalizowane zasoby, wdrażać je tak samo, jak bibliotekę w aplikacji klasycznej przy użyciu modelu koncentrator i klienci. Korzystanie z głównego pliku zasobów i wszystkich plików zlokalizowanych zasobów w Twojej [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, Dodaj odwołanie do zestawu głównego. W czasie kompilacji program Visual Studio wyodrębnia zasoby z głównego pliku zasobów i plików zasobów zlokalizowanych do oddzielnych plików resw. Następnie kompiluje pliki resw do jednego PRI pliku, który [!INCLUDE[wrt](../../../includes/wrt-md.md)] uzyskuje dostęp w czasie wykonywania.  
  
<a name="NonLoc"></a>   
## <a name="example-non-localized-includenetportableincludesnet-portable-mdmd"></a>Przykład: Niezlokalizowany [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 Poniżej prostym, niezlokalizowana [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] przykład używa zasobów do przechowywania nazw kolumn i określenie liczby znaków, aby zarezerwować na dane tabelaryczne. W przykładzie do przechowywania zasobów ciągów wymienionych w poniższej tabeli użyto pliku o nazwie LibResources.resx.  
  
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
  
 Poniższy kod definiuje `UILibrary` klasę, która używa otoki Menedżera zasobów o nazwie `resources` generowane przez program Visual Studio po **modyfikator dostępu** dla pliku jest zmieniana na **publicznych** . Klasa UILibrary analizuje dane ciągu w razie potrzeby. . Należy zauważyć, że klasa `MyCompany.Employees` przestrzeni nazw.  
  
 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]  
  
 Poniższy kod ilustruje sposób, w jaki `UILibrary` klasy i jej zasoby są dostępne z aplikacji trybu konsoli. Wymaga to dodania odwołania do pliku UILIbrary.dll do projektu aplikacji konsoli.  
  
 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]  
  
 Poniższy kod ilustruje sposób, w jaki `UILibrary` klasy i jej zasoby są dostępne z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Wymaga to dodania odwołania do pliku UILIbrary.dll do projektu aplikacji do Sklepu Windows.  
  
 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]  
  
## <a name="example-localized-includenetportableincludesnet-portable-mdmd"></a>Przykład: zlokalizowany [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 Następujące zlokalizowane [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] przykład zawiera zasoby dotyczące francuski (Francja) i angielska (Stany Zjednoczone). Kultura angielski (Stany Zjednoczone) jest domyślną kulturą aplikacji; jej zasoby są pokazane w tabeli w [poprzedniej sekcji](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). Plik zasobów dla kultury Francuski (Francja) o nazwie LibResources.fr-FR.resx składa się z zasobów ciągu wymienionych w poniższej tabeli. Kod źródłowy `UILibrary` klasy jest taka sama, jak pokazano w poprzedniej sekcji.  
  
|Nazwa zasobu|Wartość zasobu|  
|-------------------|--------------------|  
|Born|Date de naissance|  
|BornLength|20|  
|Hired|Date embauché|  
|HiredLength|16|  
|ID|ID|  
|Nazwa|Nom|  
|Tytuł|Base de données des employés|  
  
 Poniższy kod ilustruje sposób, w jaki `UILibrary` klasy i jej zasoby są dostępne z aplikacji trybu konsoli. Wymaga to dodania odwołania do pliku UILIbrary.dll do projektu aplikacji konsoli.  
  
 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]  
  
 Poniższy kod ilustruje sposób, w jaki `UILibrary` klasy i jej zasoby są dostępne z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Wymaga to dodania odwołania do pliku UILIbrary.dll do projektu aplikacji do Sklepu Windows. Używa statycznego `ApplicationLanguages.PrimaryLanguageOverride` właściwości do ustawienia aplikacji na francuską preferowanego języka.  
  
 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Resources.ResourceManager>  
- [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)  
- [Opakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
