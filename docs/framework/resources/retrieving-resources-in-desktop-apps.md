---
title: Pobieranie zasobów w aplikacjach klasycznych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- resource files, packaging
- application resources, packaging
- localization
- versioning satellite assemblies
- retrieving localized resources
- application resources, deploying
- packaging application resources
- versioning resources
- translating resources into languages
- localizing resources
ms.assetid: eca16922-1c46-4f68-aefe-e7a12283641f
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a02d9efcadcc4c7066dba4e55268ab898b6790e8
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="retrieving-resources-in-desktop-apps"></a>Pobieranie zasobów w aplikacjach klasycznych
Podczas pracy z zlokalizowanych zasobów w aplikacjach klasycznych .NET Framework, należy w idealnym przypadku pakiet zasobów dla domyślnej lub kultury neutralnej o zestawie głównym i utworzyć zestaw satelicki osobne dla każdego języka i kultury, która obsługuje aplikację. Następnie można użyć <xref:System.Resources.ResourceManager> klasy zgodnie z opisem w następnej sekcji, aby uzyskać dostęp do zasobów o nazwie. Jeśli wybierzesz nie osadzić zasobów w zestawie głównym i zestawy satelickie, można również przejść, pliki binarne .resources bezpośrednio, zgodnie z opisem w sekcji [podczas pobierania zasobów z plików .resources](#from_file) dalszej części tego artykuł.  Można pobrać zasobów w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, zobacz [tworzenie i pobieranie zasobów w aplikacjach w Sklepie Windows](http://go.microsoft.com/fwlink/p/?LinkID=241674) w Centrum deweloperów systemu Windows.  
  
<a name="from_assembly"></a>   
## <a name="retrieving-resources-from-assemblies"></a>Pobieranie zasobów z zestawów  
 <xref:System.Resources.ResourceManager> Klasy zapewnia dostęp do zasobów w czasie wykonywania. Możesz użyć <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> metoda pobierania zasoby ciągów i <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType> lub <xref:System.Resources.ResourceManager.GetStream%2A?displayProperty=nameWithType> metoda pobierania zasobów innych niż ciąg. Każda metoda ma dwa przeciążenia:  
  
-   Przeciążenia, w których pojedynczy parametr jest ciąg znaków zawierający nazwę zasobu. Metoda podejmie próbę pobrania tego zasobu dla bieżącej kultury wątku. Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, i <xref:System.Resources.ResourceManager.GetStream%28System.String%29> metody.  
  
-   Przeciążenia, który zawiera dwa parametry: ciąg zawierający nazwę zasobu oraz a <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje kultury zasobów, których ma być pobrana. Jeśli zasobów dla kultury nie można odnaleźć, Menedżer zasobów używa rezerwowej reguł można pobrać odpowiedni zasób. Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, i <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> metody.  
  
 Menedżer zasobów używa proces rezerwowy zasobów do kontrolowania sposobu aplikacja pobiera zasoby specyficzne dla kultury. Aby uzyskać więcej informacji, zobacz sekcję "Proces rezerwowy zasobów" w [pakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Aby uzyskać informacje o uruchamianiu <xref:System.Resources.ResourceManager> obiektów, zobacz sekcję "Tworzenia wystąpienia obiektu ResourceManager" w <xref:System.Resources.ResourceManager> klasy tematu.  
  
### <a name="retrieving-string-data-an-example"></a>Danych podczas pobierania ciągu: Przykład  
 Następujące przykładowe wywołania <xref:System.Resources.ResourceManager.GetString%28System.String%29> metoda pobierania zasobów ciągu bieżącej kultury interfejsu użytkownika. Francuski (Francja) i kultur rosyjski (Rosji) zawiera zasób ciągu neutralne kultury angielski (Stany Zjednoczone) i zlokalizowanych zasobów. Następujące zasoby angielski (Stany Zjednoczone) znajduje się w pliku o nazwie Strings.txt:  
  
```  
TimeHeader=The current time is  
```  
  
 Francuski (Francja) zasobów znajduje się w pliku o nazwie Strings.fr-FR.txt:  
  
```  
TimeHeader=L'heure actuelle est  
```  
  
 Zasób rosyjski (Rosji) znajduje się w pliku o nazwie Strings.ru-RU-txt:  
  
```  
TimeHeader=Текущее время —  
```  
  
 Kod źródłowy w tym przykładzie, który znajduje się w pliku o nazwie GetString.cs C# wersji kodu i GetString.vb dla używanej wersji programu Visual Basic, definiuje tablicy ciągów, która zawiera nazwę kultury cztery: trzy kultury, dla których dostępnych zasobów i kultura, hiszpański (Hiszpania). Pętli, które wykonuje pięć razy losowo wybiera jeden z tych kultur i przypisuje go do <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> i <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> właściwości. Następnie wywołuje <xref:System.Resources.ResourceManager.GetString%28System.String%29> metoda pobierania zlokalizowanego ciągu, który wyświetla wraz z porę dnia.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstring.cs#3)]
 [!code-vb[Conceptual.Resources.Retrieving#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstring.vb#3)]  
  
 Następujący plik wsadowy (bat) kompiluje przykładzie i generuje zestawów satelickich w katalogach odpowiednie. Polecenia są dostępne dla języka C# i kompilatora. W języku Visual Basic, zmień `csc` do `vbc`i zmień `GetString.cs` do `GetString.vb`.  
  
```  
resgen strings.txt  
csc GetString.cs -resource:strings.resources  
  
resgen strings.fr-FR.txt  
md fr-FR  
al -embed:strings.fr-FR.resources -culture:fr-FR -out:fr-FR\GetString.resources.dll  
  
resgen strings.ru-RU.txt  
md ru-RU  
al -embed:strings.ru-RU.resources -culture:ru-RU -out:ru-RU\GetString.resources.dll  
```  
  
 Bieżąca kultura interfejsu użytkownika po hiszpański (Hiszpania), należy pamiętać, w przykładzie przedstawiono zasoby dla języka angielskiego, ponieważ język hiszpański zasoby są niedostępne, a kulturę domyślną na przykład jest angielski.  
  
### <a name="retrieving-object-data-two-examples"></a>Podczas pobierania danych obiektu: Dwa przykłady  
 Można użyć <xref:System.Resources.ResourceManager.GetObject%2A> i <xref:System.Resources.ResourceManager.GetStream%2A> metody do pobierania danych obiektu. W tym typy danych pierwotnych, obiekty możliwe do serializacji i obiekty, które są przechowywane w formacie binarnym (np. obrazów).  
  
 W poniższym przykładzie użyto <xref:System.Resources.ResourceManager.GetStream%28System.String%29> otwarcia okna powitalny metoda pobierania mapy bitowej, który jest używany w aplikacji. Następujące źródła kodu w pliku o nazwie CreateResources.cs (dla C#) lub CreateResources.vb (w języku Visual Basic) generuje plik .resx, który zawiera seryjnych obraz. W takim przypadku załadowania obrazu z pliku o nazwie SplashScreen.jpg; można zmodyfikować nazwę pliku, aby zastąpić własnego obrazu.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/createresources.cs#4)]
 [!code-vb[Conceptual.Resources.Retrieving#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/createresources.vb#4)]  
  
 Poniższy kod pobiera zasobu i wyświetla obraz w <xref:System.Windows.Forms.PictureBox> formantu.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstream.cs#5)]
 [!code-vb[Conceptual.Resources.Retrieving#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstream.vb#5)]  
  
 Następujący plik wsadowy służy do tworzenia przykład C#. W języku Visual Basic, zmień `csc` do `vbc`i zmień rozszerzenie pliku kodu źródłowego z `.cs` do `.vb`.  
  
```  
csc CreateResources.cs  
CreateResources  
  
resgen AppResources.resx  
  
csc GetStream.cs -resource:AppResources.resources  
```  
  
 W poniższym przykładzie użyto <xref:System.Resources.ResourceManager.GetObject%28System.String%29?displayProperty=nameWithType> metodę deserializacji niestandardowych obiektów. Przykład zawiera kod źródłowy plik o nazwie UIElements.cs (UIElements.vb w języku Visual Basic), który definiuje następującą strukturę o nazwie `PersonTable`. Ta struktura jest przeznaczona do użycia przez Tabela ogólna procedura wyświetlania Wyświetla zlokalizowanych nazw kolumn tabeli. Należy pamiętać, że `PersonTable` struktura jest oznaczona atrybutem <xref:System.SerializableAttribute> atrybutu.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example.cs#6)]
 [!code-vb[Conceptual.Resources.Retrieving#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#6)]  
  
 Następujący kod w pliku o nazwie CreateResources.cs (CreateResources.vb w języku Visual Basic) tworzy plik zasobu XML o nazwie UIResources.resx, która przechowuje tytuł tabeli i `PersonTable` obiekt, który zawiera informacje dotyczące aplikacji, który jest zlokalizowany na Język angielski.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example1.cs#7)]
 [!code-vb[Conceptual.Resources.Retrieving#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#7)]  
  
 Następujący kod w pliku kodu źródłowego o nazwie GetObject.cs (GetObject.vb), a następnie pobiera zasobów i wyświetla je w konsoli.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example2.cs#8)]
 [!code-vb[Conceptual.Resources.Retrieving#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example2.vb#8)]  
  
 Możesz skompilować pliku niezbędnych zasobów i zestawów i uruchom aplikację, wykonując następujący plik wsadowy. Należy użyć `/r` opcję, aby podać Resgen.exe z odwołaniem do UIElements.dll, dzięki czemu będzie miał dostęp do informacji o `PersonTable` struktury. Jeśli używasz programu C#, Zastąp `vbc` nazwę kompilatora `csc`i Zastąp `.vb` rozszerzenie o `.cs`.  
  
```  
vbc -t:library UIElements.vb  
vbc CreateResources.vb -r:UIElements.dll  
CreateResources  
  
resgen UIResources.resx  -r:UIElements.dll  
vbc GetObject.vb -r:UIElements.dll -resource:UIResources.resources  
  
GetObject.exe  
```  
  
## <a name="versioning-support-for-satellite-assemblies"></a>Przechowywanie wersji obsługę zestawy satelickie  
 Domyślnie gdy <xref:System.Resources.ResourceManager> obiektu pobiera żądanych zasobów, wygląda na to zestawów satelickich, które mają numery wersji, spełniających numer wersji w zestawie głównym. Po wdrożeniu aplikacji, można zaktualizować zestawu głównego lub zestawy satelickie określonego zasobu. .NET Framework zapewnia obsługę wersji zestawu głównego i zestawy satelickie.  
  
 <xref:System.Resources.SatelliteContractVersionAttribute> Atrybutu zapewnia obsługę wersji zestawu głównego. Określenie ten atrybut w zestawie głównym aplikacji można zaktualizować i ponownie wdrożyć główny zestaw bez aktualizowania jego zestawy satelickie. Po zaktualizowaniu główny zestaw zwiększenie numeru wersji zestawu głównego, ale pozostawić numer wersji kontraktu satelity bez zmian. Gdy usługa resource manager pobiera żądanych zasobów, ładuje wersja zestawu satelity określony przez atrybut.  
  
 Zestawy zasad wydawcy zapewniają obsługę wersjonowanie zestawów satelickich. Możesz zaktualizować i ponownie wdrożyć zestawu satelickiego bez aktualizowania główny zestaw. Po zaktualizowaniu zestawu satelickiego zwiększenie numeru wersji i składnikiem zestaw zasad wydawcy. W zestawie zasad wydawcy, należy określić, że Twoje nowe zestawu satelickiego jest zgodny z poprzedniej wersji. Menedżer zasobów użyje <xref:System.Resources.SatelliteContractVersionAttribute> wersja zestawu satelity określone przez zasady wydawcy zostanie powiązany atrybut można ustalić wersji zestawu satelickiego, ale moduł ładujący zestawu. Aby uzyskać więcej informacji na temat zestawów zasad wydawcy, zobacz [tworzenia pliku zasad wydawcy](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md).  
  
 Aby włączyć obsługę wersji pełnego zestawu, zaleca się wdrożenie zestawy o silnych nazwach w [Globalna pamięć podręczna zestawów](../../../docs/framework/app-domains/gac.md) i wdrażanie zestawów, które nie mają silnej nazwy w katalogu aplikacji. Jeśli chcesz wdrożyć zestawy o silnych nazwach w katalogu aplikacji, nie można zwiększyć numer wersji zestawu satelickiego podczas aktualizowania zestawu. Zamiast tego należy wykonać aktualizacji w miejscu, gdzie Zamień istniejący kod zaktualizowanego kodu i zachować ten sam numer wersji. Na przykład, jeśli chcesz zaktualizować wersję 1.0.0.0 zestawu satelickiego pełni określonej nazwy zestawu "myApp.resources, wersji 1.0.0.0, Culture = de, PublicKeyToken = = b03f5f11d50a3a", zastąpić myApp.resources.dll zaktualizowane, która została skompilowana przy użyciu nazwy zestawu tego samego, w pełni określonego "myApp.resources, wersji 1.0.0.0, Culture = = de, PublicKeyToken = b03f5f11d50a3a". Należy pamiętać, że za pomocą aktualizacji w miejscu na plików zestawów satelickich utrudnia dla aplikacji dokładnie sprawdzić wersja zestawu satelickiego.  
  
 Aby uzyskać więcej informacji o wersji zestawu, zobacz [przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md) i [jak zestawy środowiska wykonawczego lokalizuje](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
<a name="from_file"></a>   
## <a name="retrieving-resources-from-resources-files"></a>Pobieranie zasobów z .resources — pliki  
 Jeśli zrezygnujesz z wdrażania zasobów w zestawy satelickie, można nadal używać <xref:System.Resources.ResourceManager> obiektu dostęp do zasobów na podstawie .resources pliki bezpośrednio. Aby to zrobić, należy wdrożyć plików .resources poprawnie. Użyć <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%2A?displayProperty=nameWithType> metody tworzenia wystąpienia <xref:System.Resources.ResourceManager> obiektu i określ katalog zawierający pliki .resources autonomicznych.  
  
### <a name="deploying-resources-files"></a>Wdrażanie .resources — pliki  
 Po osadzeniu plików .resources zestawu aplikacji i zestawy satelickie każdego zestawu satelickiego ma taką samą nazwę pliku, ale jest umieszczany w podkatalogu, które odzwierciedla zestawu satelickiego kultury. Z kolei gdy uzyskujesz dostęp do zasobów z plików .resources bezpośrednio, wszystkich plików .resources można umieścić w jednym katalogu, zwykle podkatalogiem katalogu aplikacji. Nazwa pliku .resources domyślnej aplikacji składa się z tylko nazwę katalogu głównego nie wskazuje na jego kultury (na przykład strings.resources). Zasobów dla każdego zlokalizowanych kultury są przechowywane w pliku, którego nazwa składa się z nazwy głównej następuje kultury (na przykład strings.ja.resources lub strings.de DE.resources). Na poniższej ilustracji pokazano lokalizację plików źródłowych w strukturze katalogów.  
  
 ![Katalog główny aplikacji](../../../docs/framework/resources/media/resappdir.gif "resappdir")  
Strukturę katalogu i konwencje nazewnictwa plików .resources  
  
### <a name="using-the-resource-manager"></a>Za pomocą Menedżera zasobów  
 Po utworzeniu zasobów i umieścić je w odpowiednich katalogu, Utwórz <xref:System.Resources.ResourceManager> obiekt, aby korzystać z zasobów przez wywołanie metody <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%28System.String%2CSystem.String%2CSystem.Type%29> metody. Pierwszy parametr określa nazwę katalogu głównego pliku .resources domyślnego aplikacji (będzie to "ciągi", na przykład w poprzedniej sekcji). Drugi parametr określa lokalizację zasobów ("zasobów" w poprzednim przykładzie). Trzeci parametr określa <xref:System.Resources.ResourceSet> wdrożenia do użycia. Jeśli trzeci parametr jest `null`, środowisko uruchomieniowe domyślne <xref:System.Resources.ResourceSet> jest używany.  
  
> [!NOTE]
>  Nie należy wdrażać aplikacji ASP.NET przy użyciu plików .resources autonomicznych. Może to spowodować blokowania problemy i podziały XCOPY wdrożenia. Zaleca się wdrożenie zasobów zestawy satelickie ASP.NET. Aby uzyskać więcej informacji, zobacz [Omówienie zasobów strony sieci Web programu ASP.NET](http://msdn.microsoft.com/library/0936b3b2-9e6e-4abe-9c06-364efef9dbbd).  
  
 Po można utworzyć wystąpienia <xref:System.Resources.ResourceManager> obiektu, należy użyć <xref:System.Resources.ResourceManager.GetString%2A>, <xref:System.Resources.ResourceManager.GetObject%2A>, i <xref:System.Resources.ResourceManager.GetStream%2A> metody zgodnie z wcześniejszym opisem można pobrać zasobów. Jednak pobieranie zasobów bezpośrednio z plików .resources różni się od pobieranie zasobów osadzonych z zestawów. Podczas pobierania zasobów z plików .resources <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, i <xref:System.Resources.ResourceManager.GetStream%28System.String%29> metody zawsze pobierają domyślną kulturę zasobów, niezależnie od bieżącej kultury. Aby uzyskać dostęp do zasobów bieżącej kultury albo aplikacji lub określoną kulturę, należy wywołać <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, lub <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> — metoda i określ kultury, którego zasoby mają być pobierane. Aby uzyskać dostęp do zasobów bieżącej kultury, określ wartość <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwość jako `culture` argumentu. Jeśli Menedżer zasobów nie można pobrać zasobów `culture`, używa reguł rezerwowy standardowych zasobów można pobrać odpowiednie zasoby.  
  
### <a name="an-example"></a>Przykład  
 Poniższy przykład przedstawia, jak Menedżer zasobów pobiera zasobów bezpośrednio z plików .resources. Przykład składa się z trzech plików tekstowych zasobów angielski (Stany Zjednoczone), francuski (Francja) i kultur rosyjski (Rosji). Angielski (Stany Zjednoczone) jest przykład domyślną kulturę. Jego zasobów są przechowywane w następującym pliku o nazwie Strings.txt:  
  
```  
Greeting=Hello  
Prompt=What is your name?  
```  
  
 Zasoby dla kultury francuski (Francja) są przechowywane w następującym pliku o nazwie Strings.fr-FR.txt:  
  
```  
Greeting=Bon jour  
Prompt=Comment vous appelez-vous?  
```  
  
 Zasoby dla kultury rosyjski (Rosji) są przechowywane w następującym pliku o nazwie Strings.ru-RU.txt:  
  
```  
Greeting=Здравствуйте  
Prompt=Как вас зовут?  
```  
  
 Oto przykładowy kod źródłowy. Przykład tworzy <xref:System.Globalization.CultureInfo> obiektów na język angielski (Stany Zjednoczone), angielski (Kanada), francuski (Francja) i kultur rosyjski (Rosji) i sprawia, że każdy bieżącej kultury. <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> Metody następnie dostarcza wartość <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwość jako `culture` argument można pobrać odpowiednie zasoby specyficzne dla kultury.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example3.cs#9)]
 [!code-vb[Conceptual.Resources.Retrieving#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example3.vb#9)]  
  
 Wersja języka C# przykładu można kompilować, uruchamiając następujące pliku wsadowego. Jeśli używasz programu Visual Basic, Zastąp `csc` z `vbc`i Zastąp `.cs` rozszerzenie o `.vb`.  
  
```  
Md Resources  
Resgen Strings.txt Resources\Strings.resources  
Resgen Strings.fr-FR.txt Resources\Strings.fr-FR.resources  
Resgen Strings.ru-RU.txt Resources\Strings.ru-RU.resources  
  
csc Example.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Resources.ResourceManager>  
 [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)  
 [Opakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Tworzenie i pobieranie zasobów w aplikacjach w Sklepie Windows](http://go.microsoft.com/fwlink/p/?LinkID=241674)
