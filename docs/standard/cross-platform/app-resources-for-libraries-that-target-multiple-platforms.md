---
title: Zasoby aplikacji dla bibliotek przeznaczonych do wielu platform
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 74cd3df645c2490bcf98533ca8846ddfb742f67f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Zasoby aplikacji dla bibliotek przeznaczonych do wielu platform
Można użyć programu .NET Framework [przenośnej biblioteki klas](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) projektu typu, aby upewnić się, że zasoby w bibliotekach klas jest możliwy z wielu platform. Ten typ projektu jest dostępny w [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] i elementów docelowych podzestaw przenośny bibliotece klas programu .NET Framework. Przy użyciu [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] gwarantuje, że biblioteki są dostępne z aplikacje komputerowe, aplikacje Silverlight, aplikacje Windows Phone i [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.  
  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] Projektu udostępnia tylko bardzo ograniczony podzestaw typów w <xref:System.Resources> przestrzeni nazw jest dostępne dla aplikacji, ale będzie można korzystać <xref:System.Resources.ResourceManager> klasy można pobrać zasobów. Jednak jeśli tworzysz aplikację za pomocą programu Visual Studio, należy użyć jednoznacznie otoka utworzony przez program Visual Studio zamiast <xref:System.Resources.ResourceManager> bezpośrednio klasa.  
  
 Aby utworzyć jednoznacznie otoki w programie Visual Studio, zestaw plików zasobów głównego **modyfikator dostępu** w Projektancie zasobów Visual Studio, aby **publicznego**. Spowoduje to utworzenie pliku [NazwaPlikuZasobów].designer.cs lub [NazwaPlikuZasobów].designer.vb zawierającego silnie typizowaną otokę ResourceManager. Aby uzyskać więcej informacji o korzystaniu z otoką zasobu o jednoznacznie, zobacz sekcję "Generowania silnie Typizowanej klasy zasobów" w [Resgen.exe (Generator pliku zasobów)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) tematu.  
  
## <a name="resource-manager-in-the-includenetportableincludesnet-portable-mdmd"></a>Menedżer zasobów w[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 W [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, dostęp do zasobów jest obsługiwane przez <xref:System.Resources.ResourceManager> klasy. Ponieważ typy w <xref:System.Resources> przestrzeni nazw, takich jak <xref:System.Resources.ResourceReader> i <xref:System.Resources.ResourceSet>, nie jest dostępny z [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, nie można uzyskać dostęp do zasobów.  
  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] Projekt zawiera cztery <xref:System.Resources.ResourceManager> elementy członkowskie wymienione w poniższej tabeli. Te konstruktory i metody umożliwiają utworzenie wystąpienia <xref:System.Resources.ResourceManager> obiektu i pobrać zasobów ciągu.  
  
|`ResourceManager`element członkowski|Opis|  
|------------------------------|-----------------|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Tworzy <xref:System.Resources.ResourceManager> wystąpienie do dostępu do pliku zasobów o nazwie w określonym zestawie.|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Tworzy <xref:System.Resources.ResourceManager> wystąpienia, która odnosi się do określonego typu.|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Pobiera nazwany zasób dla bieżącej kultury.|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Pobiera nazwany zasób należący do określonej kultury.|  
  
 Wykluczenie innych <xref:System.Resources.ResourceManager> członków z [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] oznacza, że serializacji obiektów, innych niż ciąg danych i obrazów nie można pobrać z pliku zasobu. Aby używać zasobów z [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], wszystkie dane obiektów należy przechowywać w postaci ciągu. Na przykład wartości liczbowe można przechowywać w pliku zasobu, konwertując je do ciągów i można je pobrać i przekonwertować je do liczby przy użyciu typu danych liczbowych `Parse` lub `TryParse` metody. Do reprezentacji w postaci ciągu można przekonwertować obrazy lub inne dane binarne przez wywołanie metody <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> — metoda i przywracania ich na bajt tablicy przez wywołanie metody <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType> metody.  
  
## <a name="the-includenetportableincludesnet-portable-mdmd-and-windows-store-apps"></a>[!INCLUDE[net_portable](../../../includes/net-portable-md.md)] i aplikacji ze Sklepu Windows  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]projekty przechowywanie zasobów w pliki resx, które następnie są kompilowane do plików .resources i osadzone w zestawie głównym lub zestawów satelickich w czasie kompilacji. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]aplikacje, z drugiej strony, wymagają zasobów, które mają być przechowywane w pobieranie plików .resw, które następnie są skompilowane w jednym pakiecie pliku indeksu (PRI) zasobu. Jednak mimo formatów plik jest niezgodny z [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] będzie działać w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.  
  
 Aby korzystać z biblioteki klas z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, Dodaj odwołanie do niej w projekcie aplikacji Sklepu Windows. Visual Studio będzie przezroczysty wyodrębniania zasoby z zestawu do plików resw i użyć go do generowania pliku PRI, z którego [!INCLUDE[wrt](../../../includes/wrt-md.md)] można wyodrębnić zasobów. W czasie wykonywania [!INCLUDE[wrt](../../../includes/wrt-md.md)] wykonuje kod w Twojej [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], ale zasobów przenośnej biblioteki klas go pobiera z pliku PRI.  
  
 Jeśli Twoje [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projekt zawiera zlokalizowane zasoby, wdrażania ich w taki sam sposób jak dla biblioteki w aplikacji klasycznej za pomocą modelu koncentrator i klienci. Aby korzystać z Twojego pliku zasobu główne i wszystkie zlokalizowane pliki zasobów w Twojej [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, Dodaj odwołanie do zestawu głównego. W czasie kompilacji program Visual Studio wyodrębnia zasoby z głównego pliku zasobów i plików zasobów zlokalizowanych do oddzielnych plików resw. Następnie kompiluje plików resw do PRI pojedynczy plik, który [!INCLUDE[wrt](../../../includes/wrt-md.md)] uzyskuje dostęp w czasie wykonywania.  
  
<a name="NonLoc"></a>   
## <a name="example-non-localized-includenetportableincludesnet-portable-mdmd"></a>Przykład: Niezlokalizowana[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 Następujące proste, niezlokalizowana [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] przykład używa zasobów do przechowywania nazw kolumn i określenie liczby znaków, aby go zarezerwować dla danych tabelarycznych. W przykładzie do przechowywania zasobów ciągów wymienionych w poniższej tabeli użyto pliku o nazwie LibResources.resx.  
  
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
  
 Poniższy kod definiuje `UILibrary` klasy, która używa otoki Menedżera zasobów o nazwie `resources` generowane przez program Visual Studio po **modyfikator dostępu** dla pliku jest zmieniana na **publicznego** . Klasa UILibrary analizuje dane ciągu w razie potrzeby. . Należy zauważyć, że klasa `MyCompany.Employees` przestrzeni nazw.  
  
 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]  
  
 Poniższy kod ilustruje sposób `UILibrary` klasy i jej zasoby są dostępne z poziomu aplikacji w trybie konsoli. Wymaga to dodania odwołania do pliku UILIbrary.dll do projektu aplikacji konsoli.  
  
 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]  
  
 Poniższy kod ilustruje sposób `UILibrary` klasy i jej zasoby są dostępne z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Wymaga to dodania odwołania do pliku UILIbrary.dll do projektu aplikacji do Sklepu Windows.  
  
 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]  
  
## <a name="example-localized-includenetportableincludesnet-portable-mdmd"></a>Przykład: zlokalizowanych[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 Następujące zlokalizowany [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] przykład zawiera zasoby dotyczące francuski (Francja) i kultur angielski (Stany Zjednoczone). Angielski (Stany Zjednoczone) kultury jest kultury domyślnej aplikacji; jej zasoby są wyświetlane w tabeli w [poprzedniej sekcji](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). Plik zasobów dla kultury Francuski (Francja) o nazwie LibResources.fr-FR.resx składa się z zasobów ciągu wymienionych w poniższej tabeli. Kod źródłowy `UILibrary` klasy jest taka sama, jak pokazano w poprzedniej sekcji.  
  
|Nazwa zasobu|Wartość zasobu|  
|-------------------|--------------------|  
|Born|Date de naissance|  
|BornLength|20|  
|Hired|Date embauché|  
|HiredLength|16|  
|ID|ID|  
|Nazwa|Nom|  
|Tytuł|Base de données des employés|  
  
 Poniższy kod ilustruje sposób `UILibrary` klasy i jej zasoby są dostępne z poziomu aplikacji w trybie konsoli. Wymaga to dodania odwołania do pliku UILIbrary.dll do projektu aplikacji konsoli.  
  
 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]  
  
 Poniższy kod ilustruje sposób `UILibrary` klasy i jej zasoby są dostępne z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Wymaga to dodania odwołania do pliku UILIbrary.dll do projektu aplikacji do Sklepu Windows. Używa statycznego `ApplicationLanguages.PrimaryLanguageOverride` właściwości do ustawienia aplikacji preferowaną danego języka na język francuski.  
  
 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Resources.ResourceManager>  
 [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)  
 [Opakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
