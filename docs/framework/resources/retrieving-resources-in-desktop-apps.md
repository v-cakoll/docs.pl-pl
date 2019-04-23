---
title: Pobieranie zasobów w aplikacjach klasycznych
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74469948ffe4045e6d367f1f60b8e66dc2a7810d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109801"
---
# <a name="retrieving-resources-in-desktop-apps"></a>Pobieranie zasobów w aplikacjach klasycznych
Podczas pracy z zlokalizowane zasoby w aplikacjach pulpitu .NET Framework, należy najlepiej pakietów zasobów dla kultury neutralnej lub domyślne przy użyciu zestawu głównego i utworzyć zestaw satelicki osobne dla każdego języka lub kultury, którą obsługuje aplikacja. Następnie można użyć <xref:System.Resources.ResourceManager> klasy zgodnie z opisem w następnej sekcji, aby uzyskać dostęp do zasobów o nazwie. Jeśli nie chcesz osadzić zasobów w głównym zestawie i zestawy satelickie, można również przejść binarnych plików Resources bezpośrednio, zgodnie z opisem w sekcji [pobieranie zasobów z plików Resources](#from_file) później w tym artykuł.  Aby pobrać zasoby w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, zobacz [tworzenie i pobieranie zasobów w aplikacjach Windows Store](https://go.microsoft.com/fwlink/p/?LinkID=241674) w Centrum deweloperów Windows.  
  
<a name="from_assembly"></a>   
## <a name="retrieving-resources-from-assemblies"></a>Pobieranie zasobów z zestawów  
 <xref:System.Resources.ResourceManager> Klasy zapewnia dostęp do zasobów w czasie wykonywania. Możesz użyć <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> metodę, aby pobranie zasobów ciągu i <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType> lub <xref:System.Resources.ResourceManager.GetStream%2A?displayProperty=nameWithType> metody do pobierania zasobów niebędących ciągami. Każda metoda charakteryzuje się dwa przeciążenia:  
  
-   Przeciążenie, którego pojedynczego parametru jest ciąg zawierający nazwę zasobu. Metoda podejmuje próbę pobrania zasobu na potrzeby bieżącej kultury wątku. Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, i <xref:System.Resources.ResourceManager.GetStream%28System.String%29> metody.  
  
-   Przeciążenia, które zawiera dwa parametry: ciąg zawierający nazwę zasobu oraz a <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje kulturę, w której zasób jest do pobrania. Jeśli zasób dla kultury nie można odnaleźć, usługi resource manager używa rezerwowej reguł można pobrać odpowiedni zasób. Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, i <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> metody.  
  
 Menedżer zasobów używa procesu bazowego zasobu do kontrolowania, jak aplikacja pobiera zasoby specyficzne dla kultury. Aby uzyskać więcej informacji, zobacz sekcję "Zasobów rezerwowych procesu" w [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Aby uzyskać informacje o uruchamianiu <xref:System.Resources.ResourceManager> obiektów, zobacz sekcję "Utworzenie wystąpienia obiektu ResourceManager" w <xref:System.Resources.ResourceManager> temat poświęcony klasie.  
  
### <a name="retrieving-string-data-an-example"></a>Trwa pobieranie danych ciągu: Przykład  
 Poniższy przykład wywołuje <xref:System.Resources.ResourceManager.GetString%28System.String%29> metodę, aby pobrać zasoby ciągu z bieżącej kultury interfejsu użytkownika. Francuski (Francja) i kultur rosyjski (Rosja) zawiera zasób w postaci ciągu neutralne kultury angielski (Stany Zjednoczone) i zlokalizowanych zasobów. Następującego zasobu języka angielskiego (Stany Zjednoczone) znajduje się w pliku o nazwie Strings.txt:  
  
```  
TimeHeader=The current time is  
```  
  
 Zasób francuski (Francja) znajduje się w pliku o nazwie Strings.fr-FR.txt:  
  
```  
TimeHeader=L'heure actuelle est  
```  
  
 Zasób rosyjski (Rosja) znajduje się w pliku o nazwie Strings.ru-RU-txt:  
  
```  
TimeHeader=Текущее время —  
```  
  
 Kod źródłowy, w tym przykładzie, który znajduje się w pliku o nazwie GetString.cs dla języka C# wersji kodu i GetString.vb dla używanej wersji programu Visual Basic, definiuje tablica ciągu, który zawiera nazwę kultury cztery: trzy kultur, dla których dostępne są zasoby i kultura, hiszpański (Hiszpania). Pętlę, która wykonuje pięć razy losowo wybiera jeden z tych kultur, a następnie przypisuje go do <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> i <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> właściwości. Następnie wywołuje <xref:System.Resources.ResourceManager.GetString%28System.String%29> metodę, która pobierze zlokalizowany ciąg zawierające oraz porze dnia.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstring.cs#3)]
 [!code-vb[Conceptual.Resources.Retrieving#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstring.vb#3)]  
  
 Następujący plik wsadowy (.bat) kompiluje przykładu i generuje zestawów satelickich w katalogach odpowiednie. Polecenia są dostarczane dla języka C# i kompilatora. Dla języka Visual Basic należy zmienić `csc` do `vbc`i zmień `GetString.cs` do `GetString.vb`.  
  
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
  
 Bieżącej kultury interfejsu użytkownika po hiszpański (Hiszpania) należy pamiętać, że w przykładzie są wyświetlane zasoby w języku angielskim, ponieważ języka hiszpańskiego zasoby są niedostępne, a język angielski jest kulturę domyślną na przykład.  
  
### <a name="retrieving-object-data-two-examples"></a>Trwa pobieranie danych z obiektu: Dwa przykłady  
 Możesz użyć <xref:System.Resources.ResourceManager.GetObject%2A> i <xref:System.Resources.ResourceManager.GetStream%2A> metody do pobierania danych z obiektu. Obejmuje to pierwotne typy danych, obiekty możliwe do serializacji i obiekty, które są przechowywane w formacie binarnym (np. obrazów).  
  
 W poniższym przykładzie użyto <xref:System.Resources.ResourceManager.GetStream%28System.String%29> otwarcia oknie powitalnym metodę, która pobierze mapy bitowej, który jest używany w aplikacji. Następujące źródła kodu w pliku o nazwie CreateResources.cs (dla C#) lub CreateResources.vb (dla języka Visual Basic) generuje plik Resx, który zawiera Zserializowany obraz. W tym przypadku obraz, który jest ładowany z pliku o nazwie SplashScreen.jpg; można zmodyfikować nazwę pliku, aby zastąpić własnego obrazu.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/createresources.cs#4)]
 [!code-vb[Conceptual.Resources.Retrieving#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/createresources.vb#4)]  
  
 Poniższy kod umożliwia pobranie zasobu i wyświetlenie obrazu w <xref:System.Windows.Forms.PictureBox> kontroli.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstream.cs#5)]
 [!code-vb[Conceptual.Resources.Retrieving#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstream.vb#5)]  
  
 Następujący plik wsadowy można użyć, aby zbudować przykład C#. Dla języka Visual Basic należy zmienić `csc` do `vbc`i zmień rozszerzenie pliku z kodem źródłowym z `.cs` do `.vb`.  
  
```  
csc CreateResources.cs  
CreateResources  
  
resgen AppResources.resx  
  
csc GetStream.cs -resource:AppResources.resources  
```  
  
 W poniższym przykładzie użyto <xref:System.Resources.ResourceManager.GetObject%28System.String%29?displayProperty=nameWithType> metodę deserializacji niestandardowych obiektów. Przykład zawiera plik kodu źródłowego o nazwie UIElements.cs (UIElements.vb dla języka Visual Basic), który definiuje następującą strukturę o nazwie `PersonTable`. Ta struktura jest przeznaczona do użycia przez procedurę wyświetlana tabela ogólna, która wyświetla zlokalizowanych nazw kolumn tabeli. Należy pamiętać, że `PersonTable` struktury jest oznaczona za pomocą <xref:System.SerializableAttribute> atrybutu.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example.cs#6)]
 [!code-vb[Conceptual.Resources.Retrieving#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#6)]  
  
 Poniższy kod w pliku o nazwie CreateResources.cs (CreateResources.vb dla języka Visual Basic) tworzy XML pliku zasobu o nazwie UIResources.resx, która przechowuje tytuł tabeli i `PersonTable` obiekt, który zawiera informacje dotyczące aplikacji, który jest zlokalizowany na Język angielski.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example1.cs#7)]
 [!code-vb[Conceptual.Resources.Retrieving#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#7)]  
  
 Następujący kod w pliku kodu źródłowego o nazwie GetObject.cs (GetObject.vb), a następnie pobiera zasoby i wyświetla je w konsoli.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example2.cs#8)]
 [!code-vb[Conceptual.Resources.Retrieving#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example2.vb#8)]  
  
 Można tworzenie zasobów niezbędnych plików i zestawów i uruchomić aplikację, wykonując następujący plik wsadowy. Należy użyć `/r` opcję, aby podać Resgen.exe z odwołaniem do UIElements.dll, aby go mogą uzyskiwać dostęp do informacji o `PersonTable` struktury. Jeśli używasz języka C#, należy zastąpić `vbc` kompilatora nazwą `csc`i Zastąp `.vb` rozszerzenie `.cs`.  
  
```  
vbc -t:library UIElements.vb  
vbc CreateResources.vb -r:UIElements.dll  
CreateResources  
  
resgen UIResources.resx  -r:UIElements.dll  
vbc GetObject.vb -r:UIElements.dll -resource:UIResources.resources  
  
GetObject.exe  
```  
  
## <a name="versioning-support-for-satellite-assemblies"></a>Obsługa przechowywania obok wersji zestawów satelickich  
 Domyślnie gdy <xref:System.Resources.ResourceManager> obiektu pobiera żądanych zasobów, wyszukuje zestawy satelickie, które mają numery wersji, która jest zgodna z liczbą wersji zestawu głównego. Po wdrożeniu aplikacji, można zaktualizować w głównym zestawie lub zestawach satelickich określonego zasobu. .NET Framework zapewnia obsługę wersji głównych zestawów i zestawów satelickich.  
  
 <xref:System.Resources.SatelliteContractVersionAttribute> Atrybutu zapewnia obsługę wersji zestawu głównego. Ten atrybut określający w głównym zestawie aplikacji pozwala na aktualizowanie i ponowne wdrażanie głównego zestawu bez aktualizowania swoich zestawów satelickich. Po zaktualizowaniu zestawu głównego zwiększenie numeru wersji zestawu głównego, ale pozostawić satelitarnej numer wersji umowy, bez zmian. Gdy usługa resource manager pobiera żądanych zasobów, ładuje wersji zestawu satelickiego określony przez atrybut.  
  
 Zestawy zasad wydawcy zapewniają obsługę wersji zestawów satelickich. Możesz zaktualizować i ponownie wdrożyć zestawu satelickiego bez aktualizowania zestawu głównego. Po zaktualizowaniu zestawu satelickiego zwiększ numer wersji i składnikiem zestaw zasad wydawcy. W zestawie zasad wydawcy, należy określić, że Twojego nowego zestawu satelickiego jest zgodne z poprzednimi wersjami z poprzednią wersją. Menedżer zasobów będzie używać <xref:System.Resources.SatelliteContractVersionAttribute> atrybutu, aby określić wersję zestawu satelickiego, ale program ładujący powiąże wersji zestawu satelickiego określone przez zasady wydawcy. Aby uzyskać więcej informacji na temat zestawów zasad wydawcy, zobacz [tworzenia plik zasad wydawcy](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md).  
  
 Aby włączyć obsługę wersji pełnego zestawu, zaleca się wdrożenie zestawy o silnych nazwach w [globalnej pamięci podręcznej](../../../docs/framework/app-domains/gac.md) i wdrażanie zestawów, które nie mają silnych nazw w katalogu aplikacji. Jeśli chcesz wdrożyć zestawów o silnej nazwie w katalogu aplikacji, nie będzie się zwiększać numer wersji zestawu satelickiego po zaktualizowaniu zestawu. Zamiast tego należy wykonać aktualizację w miejscu, gdzie Zastąp istniejący kod ze zaktualizowanym kodem i zachować ten sam numer wersji. Na przykład, jeśli chcesz zaktualizować wersję 1.0.0.0 zestawem satelickim o nazwie pełni określonego zestawu "myApp.resources i wersji 1.0.0.0, Culture = de, PublicKeyToken = = b03f5f11d50a3a", zastąpić myApp.resources.dll zaktualizowane, który został skompilowany przy użyciu nazwy same, w pełni określonego zestawu "myApp.resources i wersji 1.0.0.0, Culture = = de, PublicKeyToken = b03f5f11d50a3a". Należy pamiętać, że za pomocą aktualizacji w miejsce na pliki zestawu satelickiego utrudnia aplikację, aby dokładnie określić wersję zestawu satelickiego.  
  
 Aby uzyskać więcej informacji o wersji zestawu, zobacz [przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md) i [jak środowisko uruchomieniowe lokalizuje zestawy](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
<a name="from_file"></a>   
## <a name="retrieving-resources-from-resources-files"></a>Pobieranie zasobów z plików Resources  
 Jeśli zrezygnujesz z wdrażania zasobów w zestawach satelickich, można nadal używać <xref:System.Resources.ResourceManager> obiekt dostępu do zasobów z Resources pliki bezpośrednio. Aby to zrobić, należy wdrożyć plików Resources poprawnie. Możesz użyć <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%2A?displayProperty=nameWithType> metodę, aby utworzyć wystąpienie <xref:System.Resources.ResourceManager> obiektu i określ katalog, który zawiera pliki Resources autonomicznych.  
  
### <a name="deploying-resources-files"></a>Wdrażanie plików Resources  
 Po osadzeniu plików Resources w zestawie aplikacji i zestawy satelickie każdego zestawu satelickiego ma taką samą nazwę pliku, ale jest umieszczana w podkatalogu, który odzwierciedla kultury zestawu satelickiego. Natomiast gdy uzyskujesz dostęp do zasobów z plików Resources bezpośrednio, możesz umieścić wszystkie pliki Resources w jednym katalogu, zwykle podkatalogu katalogu aplikacji. Nazwa pliku Resources domyślnej aplikacji składa się z tylko nazwę katalogu głównego nie wskazuje na jej kultury (na przykład strings.resources). Zasoby dla każdej zlokalizowanej kultury są przechowywane w pliku o nazwie składa się z nazwy głównej kultury (na przykład strings.ja.resources lub strings.de-DE.resources). 
 
 Poniższa ilustracja przedstawia lokalizację plików źródłowych w strukturze katalogów. Daje ona również konwencje nazewnictwa dla .resource plików.  

 ![Ilustracja przedstawiająca katalog główny aplikacji.](./media/retrieving-resources-in-desktop-apps/resource-application-directory.gif)  
  
### <a name="using-the-resource-manager"></a>Przy użyciu usługi Resource Manager  
 Po utworzeniu zasobów i umieścić je w odpowiednim katalogu, możesz utworzyć <xref:System.Resources.ResourceManager> obiektu na korzystanie z zasobów przez wywołanie metody <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%28System.String%2CSystem.String%2CSystem.Type%29> metody. Pierwszy parametr określa nazwę katalogu głównego pliku Resources domyślnej aplikacji (będzie to "ciągi", na przykład w poprzedniej sekcji). Drugi parametr określa lokalizację zasobów ("zasoby" w poprzednim przykładzie). Trzeci parametr określa <xref:System.Resources.ResourceSet> wdrożenia do użycia. Jeśli trzeci parametr jest `null`, domyślne środowisko uruchomieniowe <xref:System.Resources.ResourceSet> jest używany.  
  
> [!NOTE]
>  Nie należy wdrażać aplikacji ASP.NET przy użyciu plików Resources autonomicznych. Może to powodować blokowanie wdrażania XCOPY problemy i znaki podziału. Firma Microsoft zaleca wdrażania zasobów platformy ASP.NET w zestawach satelickich. Aby uzyskać więcej informacji, zobacz [omówienie zasoby strony sieci Web programu ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100)).  
  
 Po tworzenia wystąpienia <xref:System.Resources.ResourceManager> obiektu, możesz użyć <xref:System.Resources.ResourceManager.GetString%2A>, <xref:System.Resources.ResourceManager.GetObject%2A>, i <xref:System.Resources.ResourceManager.GetStream%2A> metod, zgodnie z wcześniejszym opisem w celu pobierania zasobów. Jednak pobieranie zasobów bezpośrednio z plików Resources różni się od pobierania osadzone zasoby z zestawów. Podczas pobierania zasobów z plików Resources <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, i <xref:System.Resources.ResourceManager.GetStream%28System.String%29> metody zawsze pobierają zasobów kultury domyślnej, niezależnie od bieżącej kultury. Aby pobrać zasoby bieżącej kultury albo aplikacji lub określonej kultury, należy wywołać <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, lub <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> metodę i określić kulturę, którego zasoby mają być pobierane. Aby pobrać zasoby bieżącej kultury, określ wartość <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwość jako `culture` argumentu. Jeśli Menedżera zasobów nie można pobrać zasobów `culture`, używa reguł rezerwowego standardowych zasobów do pobierania odpowiednich zasobów.  
  
### <a name="an-example"></a>Przykład  
 W poniższym przykładzie pokazano, jak usługi resource manager pobiera zasoby, bezpośrednio z plików Resources. Przykład składa się z trzech plików zasobów w formacie tekstowym dla języka angielskiego (Stany Zjednoczone), francuski (Francja) i kultur rosyjski (Rosja). Angielski (Stany Zjednoczone) jest przykład domyślnej kultury. Jego zasobów są przechowywane w następującym pliku o nazwie Strings.txt:  
  
```  
Greeting=Hello  
Prompt=What is your name?  
```  
  
 Zasobów dla kultury francuski (Francja) są przechowywane w następującym pliku o nazwie Strings.fr-FR.txt:  
  
```  
Greeting=Bon jour  
Prompt=Comment vous appelez-vous?  
```  
  
 Zasobów dla kultury rosyjski (Rosja) są przechowywane w następującym pliku o nazwie Strings.ru-RU.txt:  
  
```  
Greeting=Здравствуйте  
Prompt=Как вас зовут?  
```  
  
 Poniżej znajduje się kod źródłowy dla przykładu. Przykład tworzy <xref:System.Globalization.CultureInfo> obiektów dla języka angielskiego (Stany Zjednoczone), angielski (Kanada), francuski (Francja) i rosyjski (Rosja) kultur i sprawia, że każdy bieżącej kultury. <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> Metoda następnie dostarcza wartość <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwość jako `culture` argumentu, aby pobrać odpowiednie zasoby specyficzne dla kultury.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example3.cs#9)]
 [!code-vb[Conceptual.Resources.Retrieving#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example3.vb#9)]  
  
 Wersja języka C# przykładu można kompilować, uruchamiając następujący plik wsadowy. Jeśli używasz języka Visual Basic, należy zastąpić `csc` z `vbc`i Zastąp `.cs` rozszerzenie `.vb`.  
  
```  
Md Resources  
Resgen Strings.txt Resources\Strings.resources  
Resgen Strings.fr-FR.txt Resources\Strings.fr-FR.resources  
Resgen Strings.ru-RU.txt Resources\Strings.ru-RU.resources  
  
csc Example.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Resources.ResourceManager>
- [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)
- [Opakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Tworzenie i pobieranie zasobów w aplikacjach Windows Store](https://go.microsoft.com/fwlink/p/?LinkID=241674)
