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
ms.openlocfilehash: 17795db2cdec419a31fe862793c88506f9535ff9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180450"
---
# <a name="retrieving-resources-in-desktop-apps"></a>Pobieranie zasobów w aplikacjach klasycznych

Podczas pracy z zlokalizowanych zasobów w .NET Framework aplikacji klasycznych, należy najlepiej spakować zasoby dla kultury domyślnej lub neutralnej z głównego zestawu i utworzyć oddzielne zestawu satelickiego dla każdego języka lub kultury, które obsługuje aplikacji. Następnie można użyć <xref:System.Resources.ResourceManager> klasy, jak opisano w następnej sekcji, aby uzyskać dostęp do nazwanych zasobów. Jeśli nie chcesz osadzać zasobów w głównym zestawie i zestawach satelitalnych, możesz również uzyskać bezpośredni dostęp do plików binarnych .resources, jak omówiono w sekcji [Pobieranie zasobów z plików .resources](#from_file) w dalszej części tego artykułu.  Aby pobrać zasoby w aplikacjach ze Sklepu Windows 8.x, zobacz [Tworzenie i pobieranie zasobów w aplikacjach ze Sklepu Windows](https://docs.microsoft.com/previous-versions/windows/apps/hh694557(v=vs.140)).  
  
<a name="from_assembly"></a>
## <a name="retrieving-resources-from-assemblies"></a>Pobieranie zasobów z zestawów  
 Klasa <xref:System.Resources.ResourceManager> zapewnia dostęp do zasobów w czasie wykonywania. Metoda służy <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> do pobierania zasobów <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType> ciągów <xref:System.Resources.ResourceManager.GetStream%2A?displayProperty=nameWithType> i lub metody do pobierania zasobów bez ciągu. Każda metoda ma dwa przeciążenia:  
  
- Przeciążenie, którego pojedynczy parametr jest ciągiem zawierającym nazwę zasobu. Metoda próbuje pobrać tego zasobu dla bieżącej kultury wątku. Aby uzyskać więcej <xref:System.Resources.ResourceManager.GetString%28System.String%29>informacji, zobacz , <xref:System.Resources.ResourceManager.GetObject%28System.String%29>i <xref:System.Resources.ResourceManager.GetStream%28System.String%29> metody.  
  
- Przeciążenie, które ma dwa parametry: ciąg zawierający nazwę <xref:System.Globalization.CultureInfo> zasobu i obiekt, który reprezentuje kulturę, której zasób ma zostać pobrany. Jeśli nie można odnaleźć zestawu zasobów dla tej kultury, menedżer zasobów używa reguł rezerwowych do pobierania odpowiedniego zasobu. Aby uzyskać więcej <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>informacji, zobacz , <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>i <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> metody.  
  
 Menedżer zasobów używa procesu rezerwowego zasobów do kontrolowania sposobu pobierania zasobów specyficznych dla kultury przez aplikację. Aby uzyskać więcej informacji, zobacz sekcję "Proces awaryjny zasobów" w sekcji [Pakowanie i wdrażanie zasobów](packaging-and-deploying-resources-in-desktop-apps.md). Aby uzyskać informacje na <xref:System.Resources.ResourceManager> temat tworzenia wystąpienia obiektu, zobacz sekcję "Tworzenie <xref:System.Resources.ResourceManager> wystąpienia obiektu ResourceManager" w temacie klasy.  
  
### <a name="retrieving-string-data-an-example"></a>Pobieranie danych ciągu: przykład  
 Poniższy przykład <xref:System.Resources.ResourceManager.GetString%28System.String%29> wywołuje metodę pobierania zasobów ciągów bieżącej kultury interfejsu użytkownika. Zawiera neutralny zasób ciąg dla kultury angielskiej (Stany Zjednoczone) i zlokalizowane zasoby dla kultur francuskich (Francja) i rosyjskich (Rosja). Następujący zasób w języku angielskim (Stany Zjednoczone) znajduje się w pliku o nazwie Strings.txt:  
  
```text
TimeHeader=The current time is  
```  
  
 Zasób francuski (Francja) znajduje się w pliku o nazwie Strings.fr-FR.txt:  
  
```text
TimeHeader=L'heure actuelle est  
```  
  
 Zasób rosyjski (Rosja) znajduje się w pliku o nazwie Strings.ru-RU-txt:  
  
```text
TimeHeader=Текущее время —  
```  
  
 Kod źródłowy w tym przykładzie, który znajduje się w pliku o nazwie GetString.cs dla wersji C# kodu i GetString.vb dla wersji Visual Basic, definiuje tablicę ciągów, która zawiera nazwę czterech kultur: trzy kultury, dla których zasoby są dostępne i kultury hiszpańskiej (Hiszpania). Pętla, która wykonuje pięć razy losowo wybiera jedną z tych <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> kultur i przypisuje go do i właściwości. Następnie wywołuje <xref:System.Resources.ResourceManager.GetString%28System.String%29> metodę, aby pobrać zlokalizowane ciąg, który wyświetla wraz z porą dnia.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstring.cs#3)]
 [!code-vb[Conceptual.Resources.Retrieving#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstring.vb#3)]  
  
 Następujący plik partii (.bat) kompiluje przykład i generuje zestawy satelickiego w odpowiednich katalogach. Polecenia są dostarczane dla języka C# i kompilatora. W przypadku języka `csc` `vbc`Visual Basic `GetString.cs` `GetString.vb`zmień na program i zmień na .  
  
```console
resgen strings.txt  
csc GetString.cs -resource:strings.resources  
  
resgen strings.fr-FR.txt  
md fr-FR  
al -embed:strings.fr-FR.resources -culture:fr-FR -out:fr-FR\GetString.resources.dll  
  
resgen strings.ru-RU.txt  
md ru-RU  
al -embed:strings.ru-RU.resources -culture:ru-RU -out:ru-RU\GetString.resources.dll  
```  
  
 Gdy bieżąca kultura interfejsu użytkownika jest hiszpański (Hiszpania), należy pamiętać, że w przykładzie wyświetla zasoby języka angielskiego, ponieważ zasoby języka hiszpańskiego są niedostępne, a angielski jest domyślną kulturą przykładu.  
  
### <a name="retrieving-object-data-two-examples"></a>Pobieranie danych obiektu: dwa przykłady  
 Można użyć <xref:System.Resources.ResourceManager.GetObject%2A> i <xref:System.Resources.ResourceManager.GetStream%2A> metody do pobierania danych obiektu. Obejmuje to prymitywne typy danych, obiekty serializable i obiekty, które są przechowywane w formacie binarnym (takich jak obrazy).  
  
 W poniższym przykładzie <xref:System.Resources.ResourceManager.GetStream%28System.String%29> użyto metody pobierania mapy bitowej, która jest używana w oknie rozprysku otwierającym aplikację. Poniższy kod źródłowy w pliku o nazwie CreateResources.cs (dla języka C#) lub CreateResources.vb (dla języka Visual Basic) generuje plik .resx zawierający obraz szeregowy. W takim przypadku obraz jest ładowany z pliku o nazwie SplashScreen.jpg; można zmodyfikować nazwę pliku, aby zastąpić własny obraz.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/createresources.cs#4)]
 [!code-vb[Conceptual.Resources.Retrieving#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/createresources.vb#4)]  
  
 Poniższy kod pobiera zasób i <xref:System.Windows.Forms.PictureBox> wyświetla obraz w formancie.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstream.cs#5)]
 [!code-vb[Conceptual.Resources.Retrieving#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstream.vb#5)]  
  
 Do utworzenia przykładu języka C# można użyć następującego pliku wsadowego. W przypadku języka `csc` `vbc`Visual Basic zmień na program , `.cs` `.vb`i zmień rozszerzenie pliku kodu źródłowego z na .  
  
```console
csc CreateResources.cs  
CreateResources  
  
resgen AppResources.resx  
  
csc GetStream.cs -resource:AppResources.resources  
```  
  
 W poniższym przykładzie <xref:System.Resources.ResourceManager.GetObject%28System.String%29?displayProperty=nameWithType> użyto metody do deserializacji obiektu niestandardowego. Przykład zawiera plik kodu źródłowego o nazwie UIElements.cs (UIElements.vb for Visual Basic), który definiuje następującą strukturę o nazwie `PersonTable`. Ta struktura jest przeznaczona do użycia przez procedurę wyświetlania tabeli ogólnej, która wyświetla zlokalizowane nazwy kolumn tabeli. Należy zauważyć, że `PersonTable` struktura <xref:System.SerializableAttribute> jest oznaczona atrybutem.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example.cs#6)]
 [!code-vb[Conceptual.Resources.Retrieving#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#6)]  
  
 Poniższy kod z pliku o nazwie CreateResources.cs (CreateResources.vb for Visual Basic) tworzy plik zasobu XML o nazwie UIResources.resx, który przechowuje tytuł tabeli i `PersonTable` obiekt zawierający informacje o aplikacji zlokalizowanej dla języka angielskiego.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example1.cs#7)]
 [!code-vb[Conceptual.Resources.Retrieving#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#7)]  
  
 Poniższy kod w pliku kodu źródłowego o nazwie GetObject.cs (GetObject.vb) następnie pobiera zasoby i wyświetla je do konsoli.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example2.cs#8)]
 [!code-vb[Conceptual.Resources.Retrieving#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example2.vb#8)]  
  
 Można utworzyć niezbędny plik zasobów i zestawy i uruchomić aplikację, wykonując następujący plik wsadowy. Należy użyć `/r` opcji, aby dostarczyć Resgen.exe z odwołaniem do UIElements.dll, aby uzyskać dostęp do informacji o `PersonTable` strukturze. Jeśli używasz języka C#, `vbc` zastąp nazwę kompilatora `csc`i zastąp `.vb` rozszerzenie . `.cs`  
  
```console
vbc -t:library UIElements.vb  
vbc CreateResources.vb -r:UIElements.dll  
CreateResources  
  
resgen UIResources.resx  -r:UIElements.dll  
vbc GetObject.vb -r:UIElements.dll -resource:UIResources.resources  
  
GetObject.exe  
```  
  
## <a name="versioning-support-for-satellite-assemblies"></a>Obsługa przechowywania wersji dla zestawów satelitarnych  
 Domyślnie, gdy <xref:System.Resources.ResourceManager> obiekt pobiera żądane zasoby, szuka zestawów satelickich, które mają numery wersji, które pasują do numeru wersji głównego zestawu. Po wdrożeniu aplikacji można zaktualizować zestaw główny lub określone zestawy satelickie zasobów. .NET Framework zapewnia obsługę wersji głównego zestawu i zestawów satelickich.  
  
 Atrybut <xref:System.Resources.SatelliteContractVersionAttribute> zapewnia obsługę przechowywania wersji dla głównego zestawu. Określenie tego atrybutu w głównym zestawie aplikacji umożliwia aktualizowanie i ponowne wdrożenie głównego zestawu bez aktualizowania jego zestawów satelickich. Po zaktualizowaniu głównego złożenia należy przyrost numeru wersji zestawu głównego, ale pozostawić numer wersji kontraktu satelitarnego bez zmian. Gdy Menedżer zasobów pobiera żądane zasoby, ładuje wersję zestawu satelickiego określoną przez ten atrybut.  
  
 Zestawy zasad wydawcy zapewniają obsługę przechowywania wersji zestawów satelickich. Można aktualizować i ponownie wdrożyć zestaw satelickiego bez aktualizowania głównego zestawu. Po zaktualizowaniu zestawu satelickiego należy przyrost jego numeru wersji i wysłać go z zestawem zasad wydawcy. W zestawie zasad wydawcy określ, że nowy zestaw satelickiego jest wstecznie zgodny z jego poprzednią wersją. Menedżer zasobów użyje <xref:System.Resources.SatelliteContractVersionAttribute> atrybutu do określenia wersji zestawu satelickiego, ale moduł ładujący zestaw będzie powiązany z wersją zestawu satelickiego określoną przez zasady wydawcy. Aby uzyskać więcej informacji na temat zestawów zasad wydawcy, zobacz [Tworzenie pliku zasad wydawcy](../configure-apps/how-to-create-a-publisher-policy.md).  
  
 Aby włączyć pełną obsługę przechowywania wersji zestawu, zaleca się wdrażanie zestawów o silnych nazwach w [globalnej pamięci podręcznej zestawów](../app-domains/gac.md) i wdrażanie zestawów, które nie mają silnych nazw w katalogu aplikacji. Jeśli chcesz wdrożyć zestawy o silnej nazwie w katalogu aplikacji, nie będzie można zwiększać numeru wersji zestawu satelickiego podczas aktualizowania zestawu. Zamiast tego należy wykonać aktualizację w miejscu, w którym można zastąpić istniejący kod zaktualizowanym kodem i zachować ten sam numer wersji. Na przykład, jeśli chcesz zaktualizować wersję 1.0.0.0 zestawu satelickiego o w pełni określonej nazwie zestawu "myApp.resources, Version=1.0.0.0, Culture=de, PublicKeyToken=b03f5f11d50a3a", należy zastąpić ją zaktualizowaną biblioteką myApp.resources.dll, która została skompilowany o tej samej, w pełni określonej nazwie zestawu "myApp.resources, Version=1.0.0.0, Culture=de, PublicKeyToken=b03f5f11d50a3a". Należy zauważyć, że za pomocą aktualizacji w miejscu na pliki zestawów satelitacyjnych utrudnia aplikacji dokładnie określić wersję zestawu satelickiego.  
  
 Aby uzyskać więcej informacji na temat przechowywania wersji zestawu, zobacz [Przechowywanie wersji zestawu](../../standard/assembly/versioning.md) i jak środowisko [wykonawcze lokalizuje zestawy](../deployment/how-the-runtime-locates-assemblies.md).  
  
<a name="from_file"></a>
## <a name="retrieving-resources-from-resources-files"></a>Pobieranie zasobów z plików .resources  
 Jeśli nie chcesz wdrażać zasobów w zestawach satelitalnych, nadal można użyć <xref:System.Resources.ResourceManager> obiektu, aby uzyskać bezpośredni dostęp do zasobów z plików .resources. Aby to zrobić, należy poprawnie wdrożyć pliki .resources. Następnie należy <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%2A?displayProperty=nameWithType> użyć metody do <xref:System.Resources.ResourceManager> wystąpienia obiektu i określić katalog, który zawiera autonomiczne pliki .resources.  
  
### <a name="deploying-resources-files"></a>Wdrażanie plików .resources  
 Podczas osadzania plików .resources w zestawie aplikacji i zestawach satelickich, każdy zestaw satelickiego ma taką samą nazwę pliku, ale jest umieszczany w podkatalogu, który odzwierciedla kulturę zestawu satelickiego. Natomiast podczas bezpośredniego uzyskiwania dostępu do zasobów z plików .resources można umieścić wszystkie pliki .resources w jednym katalogu, zwykle w podkatalogu katalogu aplikacji. Nazwa domyślnego pliku .resources aplikacji składa się tylko z nazwy głównej, bez wskazania jej kultury (na przykład strings.resources). Zasoby dla każdej zlokalizowanej kultury są przechowywane w pliku, którego nazwa składa się z nazwy głównej, po której następuje kultura (na przykład strings.ja.resources lub strings.de-DE.resources).

 Na poniższej ilustracji pokazano, gdzie pliki zasobów powinny znajdować się w strukturze katalogów. Daje również konwencje nazewnictwa dla plików .resource.  

 ![Ilustracja przedstawiająca główny katalog aplikacji.](./media/retrieving-resources-in-desktop-apps/resource-application-directory.gif)  
  
### <a name="using-the-resource-manager"></a>Korzystanie z Menedżera zasobów  
 Po utworzeniu zasobów i umieszczeniu ich w odpowiednim <xref:System.Resources.ResourceManager> katalogu, należy utworzyć obiekt <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%28System.String%2CSystem.String%2CSystem.Type%29> do użycia zasobów, wywołując metodę. Pierwszy parametr określa nazwę główną domyślnego pliku .resources aplikacji (byłoby to "ciągi" w przykładzie w poprzedniej sekcji). Drugi parametr określa lokalizację zasobów ("Zasoby" dla poprzedniego przykładu). Trzeci parametr określa <xref:System.Resources.ResourceSet> implementację do użycia. Jeśli trzecim parametrem jest `null`, <xref:System.Resources.ResourceSet> używany jest domyślny czas wykonywania.  
  
> [!NOTE]
> Nie należy wdrażać ASP.NET aplikacji przy użyciu autonomicznych plików .resources. Może to spowodować problemy z blokowaniem i przerywa wdrożenie XCOPY. Zaleca się wdrożenie ASP.NET zasobów w zestawach satelitalnych. Aby uzyskać więcej informacji, zobacz [ASP.NET Omówienie zasobów strony sieci Web](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100)).  
  
 Po <xref:System.Resources.ResourceManager> wystąpieniu obiektu należy użyć <xref:System.Resources.ResourceManager.GetString%2A>programu <xref:System.Resources.ResourceManager.GetObject%2A>, <xref:System.Resources.ResourceManager.GetStream%2A> i metod, o których wspomniano wcześniej, aby pobrać zasoby. Jednak pobieranie zasobów bezpośrednio z plików .resources różni się od pobierania osadzonych zasobów z zestawów. Podczas pobierania zasobów z plików .resources <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, <xref:System.Resources.ResourceManager.GetStream%28System.String%29> <xref:System.Resources.ResourceManager.GetString%28System.String%29>, i metody zawsze pobrać domyślne zasoby kultury, niezależnie od bieżącej kultury. Aby pobrać zasoby bieżącej kultury aplikacji lub określonej kultury, należy <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>wywołać <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>metodę <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> , lub metodę i określić kulturę, której zasoby mają zostać pobrane. Aby pobrać zasoby bieżącej kultury, należy określić <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> wartość `culture` właściwości jako argument. Jeśli Menedżer zasobów nie może `culture`pobrać zasobów programu , używa standardowych reguł rezerwowych zasobów do pobierania odpowiednich zasobów.  
  
### <a name="an-example"></a>Przykład  
 W poniższym przykładzie pokazano, jak Menedżer zasobów pobiera zasoby bezpośrednio z plików .resources. Przykład składa się z trzech tekstowych plików zasobów dla kultur angielskich (Stany Zjednoczone), francuski (Francja) i rosyjski (Rosja). Angielski (Stany Zjednoczone) jest przykładową kulturą domyślną. Jego zasoby są przechowywane w następującym pliku o nazwie Strings.txt:  
  
```text
Greeting=Hello  
Prompt=What is your name?  
```  
  
 Zasoby dla kultury francuskiej (Francja) są przechowywane w następującym pliku o nazwie Strings.fr-FR.txt:  
  
```text
Greeting=Bon jour  
Prompt=Comment vous appelez-vous?  
```  
  
 Zasoby dla kultury rosyjskiej (Rosja) są przechowywane w następującym pliku, który nosi nazwę Strings.ru-RU.txt:  
  
```text
Greeting=Здравствуйте  
Prompt=Как вас зовут?  
```  
  
 Poniżej znajduje się kod źródłowy dla przykładu. Przykład tworzy wystąpienia <xref:System.Globalization.CultureInfo> obiektów dla kultur angielski (Stany Zjednoczone), angielski (Kanada), francuski (Francja) i rosyjski (Rosja) i sprawia, że każda z bieżących kultur. Metoda <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> następnie dostarcza wartość <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwości jako `culture` argument, aby pobrać odpowiednie zasoby specyficzne dla kultury.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example3.cs#9)]
 [!code-vb[Conceptual.Resources.Retrieving#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example3.vb#9)]  
  
 Można skompilować wersję języka C# przykładu, uruchamiając następujący plik wsadowy. Jeśli używasz języka Visual `csc` Basic, zastąp `vbc`rozszerzenie i zastąp `.cs` go `.vb`.  
  
```console
Md Resources  
Resgen Strings.txt Resources\Strings.resources  
Resgen Strings.fr-FR.txt Resources\Strings.fr-FR.resources  
Resgen Strings.ru-RU.txt Resources\Strings.ru-RU.resources  
  
csc Example.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Resources.ResourceManager>
- [Zasoby w aplikacjach klasycznych](index.md)
- [Opakowanie i wdrażanie zasobów](packaging-and-deploying-resources-in-desktop-apps.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../deployment/how-the-runtime-locates-assemblies.md)
- [Tworzenie i pobieranie zasobów w aplikacjach ze Sklepu Windows](https://docs.microsoft.com/previous-versions/windows/apps/hh694557(v=vs.140))
