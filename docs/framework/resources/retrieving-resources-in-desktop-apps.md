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

W przypadku pracy z zlokalizowanymi zasobami w .NET Framework aplikacjach klasycznych najlepiej jest spakować zasoby dla kultury domyślnej lub neutralnej z zestawem głównym i utworzyć oddzielny zestaw satelicki dla każdego języka lub kultury obsługiwanej przez aplikację. Następnie można użyć <xref:System.Resources.ResourceManager> klasy zgodnie z opisem w następnej sekcji, aby uzyskać dostęp do nazwanych zasobów. Jeśli nie zdecydujesz się na osadzanie zasobów w głównym zestawie i zestawach satelickich, możesz również uzyskać dostęp do plików binarnych. resources bezpośrednio, zgodnie z opisem w sekcji [pobieranie zasobów z plików. resources](#from_file) w dalszej części tego artykułu.  Aby pobrać zasoby z aplikacji ze sklepu Windows 8. x, zobacz [Tworzenie i pobieranie zasobów w aplikacjach ze sklepu Windows](https://docs.microsoft.com/previous-versions/windows/apps/hh694557(v=vs.140)).  
  
<a name="from_assembly"></a>
## <a name="retrieving-resources-from-assemblies"></a>Pobieranie zasobów z zestawów  
 <xref:System.Resources.ResourceManager> Klasa zapewnia dostęp do zasobów w czasie wykonywania. Używasz <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> metody do pobierania zasobów ciągów i metody <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType> lub <xref:System.Resources.ResourceManager.GetStream%2A?displayProperty=nameWithType> do pobierania zasobów niebędących ciągami. Każda metoda ma dwa przeciążenia:  
  
- Przeciążenie, którego pojedynczy parametr jest ciągiem zawierającym nazwę zasobu. Metoda próbuje pobrać ten zasób dla bieżącej kultury wątku. Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager.GetString%28System.String%29>metody <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, i <xref:System.Resources.ResourceManager.GetStream%28System.String%29> .  
  
- Przeciążenie, które ma dwa parametry: ciąg zawierający nazwę zasobu oraz <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje kulturę, której zasób ma zostać pobrany. Jeśli nie można znaleźć zestawu zasobów dla tej kultury, Menedżer zasobów używa reguł powrotu do pobrania odpowiedniego zasobu. Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>metody <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, i <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> .  
  
 Menedżer zasobów używa procesu rezerwowego zasobów do kontrolowania sposobu, w jaki aplikacja pobiera zasoby specyficzne dla kultury. Aby uzyskać więcej informacji, zobacz sekcję "proces rezerwowy zasobów" w artykule [pakowanie i wdrażanie zasobów](packaging-and-deploying-resources-in-desktop-apps.md). Aby uzyskać informacje o tworzeniu wystąpienia <xref:System.Resources.ResourceManager> obiektu, zobacz sekcję "Tworzenie wystąpienia obiektu ResourceManager" w temacie dotyczącym <xref:System.Resources.ResourceManager> klas.  
  
### <a name="retrieving-string-data-an-example"></a>Pobieranie danych ciągu: przykład  
 Poniższy przykład wywołuje metodę, <xref:System.Resources.ResourceManager.GetString%28System.String%29> aby pobrać zasoby ciągów dla bieżącej kultury interfejsu użytkownika. Zawiera on neutralny zasób ciągu dla kultur angielskiej (Stany Zjednoczone) i zlokalizowanych zasobów dla kultur francuski (Francja) i rosyjski (Rosja). Następujący zasób w języku angielskim (Stany Zjednoczone) znajduje się w pliku o nazwie Strings. txt:  
  
```text
TimeHeader=The current time is  
```  
  
 Zasób francuski (Francja) znajduje się w pliku o nazwie Strings.fr-FR. txt:  
  
```text
TimeHeader=L'heure actuelle est  
```  
  
 Zasób rosyjski (Rosja) znajduje się w pliku o nazwie Strings.ru-RU-txt:  
  
```text
TimeHeader=Текущее время —  
```  
  
 Kod źródłowy tego przykładu, który znajduje się w pliku o nazwie GetString.cs dla wersji C# kodu i GetString. vb dla wersji Visual Basic, definiuje tablicę ciągów, która zawiera nazwę czterech kultur: trzy kultury, dla których dostępne są zasoby i kulturę hiszpańskią (Hiszpania). Pętla, która wykonuje pięć razy losowo wybiera jedną z tych kultur i przypisuje ją <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> do <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> właściwości i. Następnie wywołuje <xref:System.Resources.ResourceManager.GetString%28System.String%29> metodę w celu pobrania zlokalizowanego ciągu, który jest wyświetlany wraz z godziną.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstring.cs#3)]
 [!code-vb[Conceptual.Resources.Retrieving#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstring.vb#3)]  
  
 Poniższy plik wsadowy (. bat) kompiluje przykład i generuje zestawy satelickie w odpowiednich katalogach. Polecenia są dostępne dla języka C# i kompilatora. W przypadku Visual Basic Zmień `csc` na `vbc`i przejdź `GetString.cs` do `GetString.vb`.  
  
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
  
 Gdy bieżącą kulturą interfejsu użytkownika jest hiszpański (Hiszpania), należy zauważyć, że w przykładzie są wyświetlane zasoby języka angielskiego, ponieważ nie są dostępne zasoby języka hiszpańskiego, a język angielski jest domyślną kulturą przykładu.  
  
### <a name="retrieving-object-data-two-examples"></a>Pobieranie danych obiektu: dwa przykłady  
 Możesz użyć metod <xref:System.Resources.ResourceManager.GetObject%2A> i <xref:System.Resources.ResourceManager.GetStream%2A> , aby pobrać dane obiektu. Obejmuje to pierwotne typy danych, obiekty, które można serializować i obiekty, które są przechowywane w formacie binarnym (na przykład obrazy).  
  
 W poniższym przykładzie użyto <xref:System.Resources.ResourceManager.GetStream%28System.String%29> metody do pobrania mapy bitowej używanej w oknie powitalnym otwierającym aplikację. Następujący kod źródłowy w pliku o nazwie CreateResources.cs (dla języka C#) lub. vb (dla Visual Basic) generuje plik resx zawierający serializowany obraz. W takim przypadku obraz jest ładowany z pliku o nazwie SplashScreen. jpg; Możesz zmodyfikować nazwę pliku, aby zastąpić własny obraz.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/createresources.cs#4)]
 [!code-vb[Conceptual.Resources.Retrieving#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/createresources.vb#4)]  
  
 Poniższy kod pobiera zasób i wyświetla obraz w <xref:System.Windows.Forms.PictureBox> kontrolce.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstream.cs#5)]
 [!code-vb[Conceptual.Resources.Retrieving#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstream.vb#5)]  
  
 Możesz użyć poniższego pliku wsadowego, aby skompilować przykład w języku C#. W przypadku Visual Basic Zmień `csc` na `vbc`i Zmień rozszerzenie pliku kodu źródłowego z `.cs` na. `.vb`  
  
```console
csc CreateResources.cs  
CreateResources  
  
resgen AppResources.resx  
  
csc GetStream.cs -resource:AppResources.resources  
```  
  
 Poniższy przykład używa <xref:System.Resources.ResourceManager.GetObject%28System.String%29?displayProperty=nameWithType> metody do deserializacji obiektu niestandardowego. Przykład zawiera plik kodu źródłowego o nazwie UIElements.cs (UIElement. vb dla Visual Basic), który definiuje następującą strukturę o nazwie `PersonTable`. Ta struktura jest przeznaczona do użycia przez ogólną procedurę wyświetlania tabeli, która wyświetla zlokalizowane nazwy kolumn tabeli. Należy zauważyć, `PersonTable` że struktura jest oznaczona przy <xref:System.SerializableAttribute> użyciu atrybutu.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example.cs#6)]
 [!code-vb[Conceptual.Resources.Retrieving#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#6)]  
  
 Poniższy kod z pliku o nazwie CreateResources.cs (UIResources. vb for Visual Basic) tworzy plik zasobów XML o nazwie Resources. resx, który przechowuje tytuł tabeli i `PersonTable` obiekt, który zawiera informacje dla aplikacji zlokalizowanej dla języka angielskiego.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example1.cs#7)]
 [!code-vb[Conceptual.Resources.Retrieving#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#7)]  
  
 Poniższy kod w pliku z kodem źródłowym o nazwie GetObject.cs (GetObject. vb) pobiera zasoby i wyświetla je w konsoli programu.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example2.cs#8)]
 [!code-vb[Conceptual.Resources.Retrieving#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example2.vb#8)]  
  
 Możesz skompilować wymagany plik zasobów i zestawy i uruchomić aplikację, wykonując następujący plik wsadowy. Musisz użyć opcji, `/r` aby dostarczyć Resgen. exe z odwołaniem do biblioteki UIElement. dll, aby można było uzyskać dostęp do informacji o `PersonTable` strukturze. Jeśli używasz języka C# `vbc` , Zamień nazwę `csc`kompilatora na i Zastąp `.vb` rozszerzenie symbolem. `.cs`  
  
```console
vbc -t:library UIElements.vb  
vbc CreateResources.vb -r:UIElements.dll  
CreateResources  
  
resgen UIResources.resx  -r:UIElements.dll  
vbc GetObject.vb -r:UIElements.dll -resource:UIResources.resources  
  
GetObject.exe  
```  
  
## <a name="versioning-support-for-satellite-assemblies"></a>Obsługa obsługi wersji dla zestawów satelickich  
 Domyślnie, gdy <xref:System.Resources.ResourceManager> obiekt pobiera żądane zasoby, szuka zestawów satelickich, które mają numery wersji zgodne z numerem wersji głównego zestawu. Po wdrożeniu aplikacji może być konieczne zaktualizowanie zestawu głównego lub określonych zestawów satelickich zasobów. .NET Framework zapewnia obsługę wersji zestawu głównego i zestawów satelickich.  
  
 Ten <xref:System.Resources.SatelliteContractVersionAttribute> atrybut zapewnia obsługę przechowywania wersji dla zestawu głównego. Określenie tego atrybutu w głównym zestawie aplikacji umożliwia aktualizowanie i ponowne wdrażanie zestawu głównego bez aktualizowania zestawów satelickich. Po zaktualizowaniu zestawu głównego należy zwiększyć numer wersji zestawu głównego, ale pozostawić numer wersji kontraktu satelitarnego bez zmian. Gdy Menedżer zasobów pobiera żądane zasoby, ładuje wersję zestawu satelickiego określoną przez ten atrybut.  
  
 Zestawy zasad wydawcy zapewniają obsługę wersji dla zestawów satelickich. Można zaktualizować i ponownie wdrożyć zestaw satelicki bez aktualizowania zestawu głównego. Po zaktualizowaniu zestawu satelickiego Zwiększ jego numer wersji i wyślij go z zestawem zasad wydawcy. W zestawie zasad wydawcy Określ, że nowy zestaw satelicki jest zgodny z poprzednią wersją. Menedżer zasobów użyje <xref:System.Resources.SatelliteContractVersionAttribute> atrybutu, aby określić wersję zestawu satelickiego, ale moduł ładujący zestawu zostanie powiązany z wersją zestawu satelickiego określoną przez zasady wydawcy. Aby uzyskać więcej informacji na temat zestawów zasad wydawcy, zobacz [Tworzenie pliku zasad wydawcy](../configure-apps/how-to-create-a-publisher-policy.md).  
  
 Aby włączyć obsługę pełnej wersji zestawu, zalecamy wdrożenie zestawów o silnych nazwach w [globalnej pamięci podręcznej zestawów](../app-domains/gac.md) i wdrażanie zestawów, które nie mają silnych nazw w katalogu aplikacji. Jeśli chcesz wdrożyć zestawy o silnych nazwach w katalogu aplikacji, nie będzie można zwiększyć numeru wersji zestawu satelickiego podczas aktualizowania zestawu. Zamiast tego należy wykonać aktualizację w miejscu, w której Zastąp istniejący kod zaktualizowanym kodem i zachować ten sam numer wersji. Na przykład jeśli chcesz zaktualizować wersję 1.0.0.0 zestawu satelickiego za pomocą w pełni określonej nazwy zestawu "MojaApl. resources, Version = 1.0.0.0, Culture = de, PublicKeyToken = b03f5f11d50a3a", Zastąp ją zainstalowaną wersją MojaApl. resources. dll, która została skompilowana z tą samą, w pełni określoną nazwą zestawu "MojaApl. resources, Version = 1.0.0.0 Należy pamiętać, że używanie aktualizacji w miejscu w plikach zestawu satelickiego utrudnia aplikacji dokładne określenie wersji zestawu satelickiego.  
  
 Aby uzyskać więcej informacji o wersji zestawu, zobacz [przechowywanie wersji zestawu](../../standard/assembly/versioning.md) i [jak środowisko uruchomieniowe lokalizuje zestawy](../deployment/how-the-runtime-locates-assemblies.md).  
  
<a name="from_file"></a>
## <a name="retrieving-resources-from-resources-files"></a>Pobieranie zasobów z plików Resources  
 Jeśli nie zdecydujesz się na wdrażanie zasobów w zestawach satelickich, możesz nadal używać <xref:System.Resources.ResourceManager> obiektu do bezpośredniego dostępu do zasobów z plików. resources. W tym celu należy poprawnie wdrożyć pliki resources. Następnie użyj <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%2A?displayProperty=nameWithType> metody, aby utworzyć wystąpienie <xref:System.Resources.ResourceManager> obiektu i określić katalog, który zawiera pliki Standalone. resources.  
  
### <a name="deploying-resources-files"></a>Wdrażanie plików Resources  
 Po osadzeniu plików Resources w zestawie aplikacji i w zestawach satelickich każdy zestaw satelicki ma taką samą nazwę pliku, ale jest umieszczany w podkatalogu, który odzwierciedla kulturę zestawu satelickiego. Natomiast w przypadku uzyskiwania dostępu do zasobów z plików resources bezpośrednio można umieścić wszystkie pliki resources w jednym katalogu, zazwyczaj podkatalogiem katalogu aplikacji. Nazwa domyślnego pliku Resources aplikacji składa się tylko z nazwy głównej, bez wskazania jego kultury (na przykład ciągi. resources). Zasoby dla każdej zlokalizowanej kultury są przechowywane w pliku, którego nazwa składa się z nazwy głównej, po której następuje kultura (na przykład ciągi. ja. resources lub strings.de-DE. resources).

 Na poniższej ilustracji przedstawiono, gdzie pliki zasobów powinny znajdować się w strukturze katalogów. Zapewnia również konwencje nazewnictwa dla plików zasobów.  

 ![Ilustracja przedstawiająca katalog główny aplikacji.](./media/retrieving-resources-in-desktop-apps/resource-application-directory.gif)  
  
### <a name="using-the-resource-manager"></a>Korzystanie z Menedżer zasobów  
 Po utworzeniu zasobów i umieszczeniu ich w odpowiednim katalogu należy utworzyć <xref:System.Resources.ResourceManager> obiekt do korzystania z zasobów, wywołując <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%28System.String%2CSystem.String%2CSystem.Type%29> metodę. Pierwszy parametr określa nazwę główną domyślnego pliku Resources aplikacji ("ciągi" dla przykładu w poprzedniej sekcji). Drugi parametr określa lokalizację zasobów ("zasoby" dla poprzedniego przykładu). Trzeci parametr określa <xref:System.Resources.ResourceSet> implementację do użycia. Jeśli trzeci parametr jest `null`, używane jest domyślne środowisko <xref:System.Resources.ResourceSet> uruchomieniowe.  
  
> [!NOTE]
> Nie Wdrażaj aplikacji ASP.NET przy użyciu autonomicznych plików Resources. Może to spowodować problemy z blokowaniem i uszkodzenie wdrożenia XCOPY. Zalecamy wdrożenie zasobów ASP.NET w zestawach satelickich. Aby uzyskać więcej informacji, zobacz [Omówienie zasobów strony sieci Web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100)).  
  
 Po <xref:System.Resources.ResourceManager> utworzeniu wystąpienia obiektu należy użyć <xref:System.Resources.ResourceManager.GetString%2A>metod, i <xref:System.Resources.ResourceManager.GetObject%2A> <xref:System.Resources.ResourceManager.GetStream%2A> , jak wspomniano wcześniej, aby pobrać zasoby. Jednak pobieranie zasobów bezpośrednio z plików Resources różni się od pobierania zasobów osadzonych z zestawów. Podczas pobierania zasobów z plików. resources metody <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, i <xref:System.Resources.ResourceManager.GetStream%28System.String%29> zawsze pobierają domyślne zasoby kultury, niezależnie od bieżącej kultury. Aby pobrać zasoby bieżącej kultury lub określonej kultury aplikacji, należy wywołać metodę <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, lub <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> i określić kulturę, której zasoby mają być pobrane. Aby pobrać zasoby bieżącej kultury, określ wartość <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwości jako `culture` argument. Jeśli Menedżer zasobów nie może pobrać zasobów programu `culture`, program użyje standardowych reguł rezerwowych zasobów do pobrania odpowiednich zasobów.  
  
### <a name="an-example"></a>Przykład  
 Poniższy przykład ilustruje sposób pobierania przez Menedżera zasobów zasobów bezpośrednio z plików Resources. Przykład składa się z trzech plików zasobów tekstowych dla kultur angielskiej (Stany Zjednoczone), francuski (Francja) i rosyjski (Rosja). W języku angielskim (Stany Zjednoczone) jest domyślną kulturą przykładową. Jego zasoby są przechowywane w następującym pliku o nazwie Strings. txt:  
  
```text
Greeting=Hello  
Prompt=What is your name?  
```  
  
 Zasoby dla kultury francuskiej (Francja) są przechowywane w następującym pliku o nazwie Strings.fr-FR. txt:  
  
```text
Greeting=Bon jour  
Prompt=Comment vous appelez-vous?  
```  
  
 Zasoby dla kultury rosyjskiej (Rosja) są przechowywane w następującym pliku o nazwie Strings.ru-RU. txt:  
  
```text
Greeting=Здравствуйте  
Prompt=Как вас зовут?  
```  
  
 Poniżej znajduje się kod źródłowy dla przykładu. Przykład tworzy wystąpienie <xref:System.Globalization.CultureInfo> obiektów dla kultur angielskiej (Stany Zjednoczone), angielski (Kanada), francuski (Francja) i rosyjski (Rosja) i tworzy każdą bieżącą kulturę. Następnie <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> Metoda dostarcza wartość <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwości jako `culture` argument do pobierania odpowiednich zasobów specyficznych dla kultury.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example3.cs#9)]
 [!code-vb[Conceptual.Resources.Retrieving#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example3.vb#9)]  
  
 Wersję języka C# można skompilować, uruchamiając następujący plik wsadowy. Jeśli używasz Visual Basic, `csc` Zamień je `vbc` `.cs` na, a następnie zastąp rozszerzenie. `.vb`  
  
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
- [Tworzenie i pobieranie zasobów w aplikacjach ze sklepu Windows](https://docs.microsoft.com/previous-versions/windows/apps/hh694557(v=vs.140))
