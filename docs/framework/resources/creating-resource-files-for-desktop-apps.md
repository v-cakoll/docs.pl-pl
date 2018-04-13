---
title: Tworzenie plików zasobów dla aplikacji klasycznych
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
- resource files, .resources files
- .resources files
- application resources, creating files
- resource files, creating
ms.assetid: 6c5ad891-66a0-4e7a-adcf-f41863ba6d8d
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b73520dfc3d5123aedce77254f738a61a27ccd95
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="creating-resource-files-for-desktop-apps"></a>Tworzenie plików zasobów dla aplikacji klasycznych
Zasoby, takie jak ciągi, obrazy lub obiektu danych, można uwzględnić w plikach zasobów, aby były łatwo dostępne dla aplikacji. .NET Framework zapewnia pięć sposoby tworzenia plików zasobów:  
  
-   Utwórz plik tekstowy zawierający zasoby ciągów. Można użyć [Generator pliku zasobów (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) do konwertowania pliku tekstowego na plik zasobów binarnych (.resources). Następnie można osadzać plików binarnych zasobu w bibliotece aplikacji lub plik wykonywalny aplikacji przy użyciu kompilatora języka lub osadzenia w zestawie satelickim przy użyciu [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Aby uzyskać więcej informacji, zobacz [zasobów w plikach tekstowych](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#TextFiles) sekcji.  
  
-   Utwórz plik zasobu (resx) XML, który zawiera ciąg, obrazu lub danych obiektu. Można użyć [Generator pliku zasobów (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) do konwertowania pliku .resx w plik zasobu binarnego (.resources). Następnie można osadzać plików binarnych zasobu w bibliotece aplikacji lub plik wykonywalny aplikacji przy użyciu kompilatora języka lub osadzenia w zestawie satelickim przy użyciu [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Aby uzyskać więcej informacji, zobacz [zasobów w plikach .resx](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResxFiles) sekcji.  
  
-   Utwórz plik zasobu (resx) XML programowo przy użyciu typów w <xref:System.Resources> przestrzeni nazw. Można utworzyć pliku .resx, wyliczyć zasobów i pobrać określonych zasobów według nazwy. Aby uzyskać więcej informacji, zobacz temat [Praca z programowo pliki resx](../../../docs/framework/resources/working-with-resx-files-programmatically.md).  
  
-   Utwórz plik zasobu binarnego (.resources) programowo. Następnie można osadzać pliku w bibliotece aplikacji lub plik wykonywalny aplikacji przy użyciu kompilatora języka lub osadzenia w zestawie satelickim przy użyciu [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Aby uzyskać więcej informacji, zobacz [zasobów plików .resources](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles) sekcji.  
  
-   Aby utworzyć plik zasobów i uwzględnić go w projekcie, należy użyć programu Visual Studio. Program Visual Studio udostępnia edytora zasobów, które umożliwia dodawanie, usuwanie i modyfikowanie zasobów. W czasie kompilacji pliku zasobów jest automatycznie przekonwertowane do pliku binarnego .resources i osadzone w zestawie aplikacji lub zestawu satelickiego. Aby uzyskać więcej informacji, zobacz [pliki zasobów w programie Visual Studio](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles) sekcji.  
  
<a name="TextFiles"></a>   
## <a name="resources-in-text-files"></a>Zasoby w plikach tekstowych  
 Pliki tekstowe (txt lub .restext) służy do przechowywania zasobów ciągów. pliki .resx lub utwórz je programowo dla zasobów innych niż ciąg. Pliki tekstowe zawierające zasoby ciągów mają następujący format:  
  
```  
# This is an optional comment.  
name = value  
  
; This is another optional comment.  
name = value  
  
; The following supports conditional compilation if X is defined.  
#ifdef X  
name1=value1  
name2=value2  
#endif  
  
# The following supports conditional compilation if Y is undefined.  
#if !Y  
name1=value1  
name2=value2  
#endif  
```  
  
 Format pliku zasobu plików txt i .restext jest identyczne. Rozszerzenie pliku .restext służy jedynie dokonanie plików tekstowych bezpośrednio do zidentyfikowania jako plików tekstowych zasobów.  
  
 Zasoby ciągów są wyświetlane jako *nazwa/wartość* pary, gdzie *nazwa* jest ciąg identyfikujący zasób, i *wartość* jest ciągu zasobu, która jest zwracana podczas przekazywania *nazwa* do metody pobierania zasobów, takich jak <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>. *Nazwa* i *wartość* muszą być rozdzielone znakiem równości (=). Na przykład:  
  
```  
FileMenuName=File  
EditMenuName=Edit  
ViewMenuName=View  
HelpMenuName=Help  
```  
  
> [!CAUTION]
>  Pliki zasobów nie należy używać do przechowywania haseł, informacji poufnych lub dane prywatne.  
  
 Puste ciągi (to znaczy zasobów, którego wartość jest <xref:System.String.Empty?displayProperty=nameWithType>) są dozwolone w plikach tekstowych. Na przykład:  
  
```  
EmptyString=  
```  
  
 Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], pliki tekstowe obsługuje kompilacji warunkowej z `#ifdef` *symbol*... `#endif` i `#if !` *symbol*... `#endif` konstrukcje. Następnie można użyć `/define` przełącznik z [Generator pliku zasobów (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) do definiowania symboli. Każdy zasób wymaga własnego `#ifdef` *symbol*... `#endif` lub `#if !` *symbol*... `#endif` utworzenia. Jeśli używasz `#ifdef` instrukcji i *symbol* jest zdefiniowana, skojarzonych zasobów znajduje się w pliku .resources; w przeciwnym razie nie jest dołączony. Jeśli używasz `#if !` instrukcji i *symbol* jest niezdefiniowana, skojarzonych zasobów znajduje się w pliku .resources; w przeciwnym razie nie jest dołączony.  
  
 Komentarze są opcjonalne w plikach tekstowych i jest poprzedzony znakiem średnika (;) lub znakiem krzyżyka (#) na początku wiersza. Wiersze zawierające komentarze można umieścić dowolne miejsce w pliku. Komentarze nie znajdują się w pliku .resources skompilowane, który jest tworzony przy użyciu [Generator pliku zasobów (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).  
  
 Pustych wierszy w plikach tekstowych są traktowane jako białe i są ignorowane.  
  
 W poniższym przykładzie zdefiniowano dwa zasoby ciągu o nazwie `OKButton` i `CancelButton`.  
  
```  
#Define resources for buttons in the user interface.  
OKButton=OK  
CancelButton=Cancel  
```  
  
 Jeśli plik zawiera zduplikowane wystąpienia *nazwa*, [Generator pliku zasobów (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) wyświetla ostrzeżenie i ignoruje nazwę drugiego.  
  
 *wartość* nie może zawierać znaków nowego wiersza, ale można użyć znaków wyjścia w stylu języka C, takich jak `\n` do reprezentowania znakiem nowego wiersza i `\t` do reprezentowania na karcie. Mogą również obejmować ukośnikiem odwrotnym, jeśli zostanie zmienione jego znaczenie (na przykład "\\\\"). Ponadto dozwolone jest pustym ciągiem.  
  
 Zasoby należy zapisać w formacie pliku tekstowego, przy użyciu kodowania UTF-8 lub UTF-16 kodowania w każdej kolejności bajtów little endian lub big-endian. Jednak [Generator pliku zasobów (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md), który konwertuje plik txt w pliku .resources traktuje pliki jako UTF-8 domyślnie. Jeśli chcesz Resgen.exe do rozpoznawania plików, które zostały zakodowane przy użyciu UTF-16, musi zawierać znacznika kolejności bajtów Unicode (U + FEFF) na początku pliku.  
  
 Aby osadzić pliku zasobów w formacie tekstowym w ramach zestawu .NET Framework, należy przekonwertować go na plik zasobów binarnych (.resources) przy użyciu [Generator pliku zasobów (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md). Można następnie Osadź plik .resources w zestawu .NET Framework za pomocą kompilatora języka lub ją osadzić w zestawie satelickim przy użyciu [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
 W poniższym przykładzie użyto pliku zasobu w formacie tekstowym o nazwie GreetingResources.txt dla prostej aplikacji konsoli "Hello World". Plik tekstowy definiuje dwa ciągi `prompt` i `greeting`, które monituje użytkownika o wprowadź jej nazwę i wyświetlić kartka z życzeniami.  
  
```  
# GreetingResources.txt   
# A resource file in text format for a "Hello World" application.  
#  
# Initial prompt to the user.  
prompt=Enter your name:   
# Format string to display the result.  
greeting=Hello, {0}!  
```  
  
 Plik tekstowy jest konwertowana na plik .resources za pomocą następującego polecenia:  
  
 **GreetingResources.txt ResGen**  
  
 Poniższy przykład przedstawia kod źródłowy aplikacji konsoli, która używa pliku .resources do wyświetlania komunikatów dla użytkownika.  
  
 [!code-csharp[Conceptual.Resources.TextFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.textfiles/cs/greeting.cs#1)]
 [!code-vb[Conceptual.Resources.TextFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.textfiles/vb/greeting.vb#1)]  
  
 Jeśli używasz programu Visual Basic i pliku kodu źródłowego nosi nazwę Greeting.vb, poniższe polecenie tworzy plik wykonywalny, który zawiera plik embedded .resources:  
  
```console 
vbc greeting.vb -resource:GreetingResources.resources
```
  
 Jeśli używasz języka C# i pliku kodu źródłowego nosi nazwę Greeting.cs, poniższe polecenie tworzy plik wykonywalny, który zawiera plik embedded .resources:  
  
 ```console
csc greeting.cs -resource:GreetingResources.resources
```
  
<a name="ResxFiles"></a>   
## <a name="resources-in-resx-files"></a>Zasoby w pliki .resx  
 W przeciwieństwie do plików tekstowych, które można przechowywać tylko zasoby ciągów, XML, pliki zasobów (resx) może przechowywać ciągi, danych binarnych, takich jak obrazy, ikony i klipów audio i obiekty programowe. Standardowy nagłówek, który opisuje format wpisów zasobów i zawiera informacje o wersji XML, który jest używany do analizowania danych zawiera plik .resx. Dane pliku zasobu następuje nagłówka XML. Każdy element danych składa się z pary nazwa/wartość, która jest zawarta w `data` tagu. Jego `name` atrybut definiuje nazwę zasobu, a zagnieżdżone `value` tag zawiera wartość zasobów. W przypadku danych ciągu `value` tag zawiera ciąg.  
  
 Na przykład następująca `data` tag definiuje zasób ciągu o nazwie `prompt` o wartości "Wprowadź nazwę:".  
  
```xml  
<data name="prompt" xml:space="preserve">  
  <value>Enter your name:</value>  
</data>  
```  
  
> [!WARNING]
>  Pliki zasobów nie należy używać do przechowywania haseł, informacji poufnych lub dane prywatne.  
  
 Dla obiektów zasobów **danych** zawiera tag `type` atrybut, który wskazuje typ danych zasobu. Dla obiektów, które składają się z danych binarnych `data` tag zawiera również `mimetype` atrybut, który wskazuje `base64` typu danych binarnych.  
  
> [!NOTE]
>  Wszystkie pliki resx Użyj elementu formatującego serializacji binarnej do generowania i analizowania danych binarnych dla określonego typu. W związku z tym pliku .resx może stać się nieprawidłowy, jeśli zmieni się w sposób niezgodny format serializacji binarnej dla obiekt.  
  
 W poniższym przykładzie przedstawiono część pliku .resx, który zawiera <xref:System.Int32> zasobów i obraz mapy bitowej.  
  
```xml  
<data name="i1" type="System.Int32, mscorlib">  
  <value>20</value>  
</data>  
  
<data name="flag" type="System.Drawing.Bitmap, System.Drawing,     
    Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"   
    mimetype="application/x-microsoft.net.object.bytearray.base64">  
  <value>  
    AAEAAAD/////AQAAAAAAAAAMAgAAADtTeX…  
  </value>  
</data>  
```  
  
> [!IMPORTANT]
>  Ponieważ pliki .resx musi składać się z poprawnie sformułowany plik XML w formacie wstępnie zdefiniowane, nie zaleca się praca z plikami .resx ręcznie, szczególnie w przypadku, gdy pliki resx zawierają zasobów niż ciągi. Zamiast tego program Visual Studio udostępnia przezroczysty interfejs do tworzenia i manipulowanie plikami .resx; Aby uzyskać więcej informacji, zobacz [pliki zasobów w programie Visual Studio](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles) sekcji. Można również tworzyć i manipulowanie plikami .resx programowo. Aby uzyskać więcej informacji, zobacz [Praca z programowo pliki resx](../../../docs/framework/resources/working-with-resx-files-programmatically.md).  
  
<a name="ResourcesFiles"></a>   
## <a name="resources-in-resources-files"></a>Zasoby w .resources — pliki  
 Można użyć <xref:System.Resources.ResourceWriter?displayProperty=nameWithType> klasy programowo utworzyć plik zasobu binarnego (.resources) bezpośrednio z kodu. Można również użyć [Generator pliku zasobów (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) utworzyć plik .resources z pliku tekstowego lub z pliku resx. Plik .resources może zawierać dane binarne (tablice typu byte) i dane obiektu oprócz danych ciągu. Programowe tworzenie pliku .resources wymaga wykonania następujących czynności:  
  
1.  Utwórz <xref:System.Resources.ResourceWriter> obiekt o unikatowej nazwy pliku. Można to zrobić, podając nazwę pliku lub strumienia pliku do <xref:System.Resources.ResourceWriter> konstruktora klasy.  
  
2.  Wywoływanie jednego z przeciążeń <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> zasobów do dodania do pliku o nazwie metody dla każdego. Zasób może być ciągiem, obiekt lub kolekcji danych binarnych (tablicę bajtów).  
  
3.  Wywołanie <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> metody, aby zapisać do pliku zasobów i zamknąć <xref:System.Resources.ResourceWriter> obiektu.  
  
> [!NOTE]
>  Pliki zasobów nie należy używać do przechowywania haseł, informacji poufnych lub dane prywatne.  
  
 Poniższy przykład tworzy programowo plik .resources o nazwie CarResources.resources, która przechowuje sześć ciągów, ikony i dwa obiekty zdefiniowane przez aplikację (dwie `Automobile` obiektów). Należy pamiętać, że `Automobile` klasy, która jest zdefiniowana i w tym przykładzie, jest oznaczane <xref:System.SerializableAttribute> atrybut, który umożliwi utrwalone przez program formatujący serializacji binarnej.  
  
 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]  
  
 Po utworzeniu pliku .resources można osadzić ją w bibliotece lub pliku wykonywalnego środowiska wykonawczego przez kompilator języka w tym `/resource` przełącznika lub ją osadzić w zestawie satelickim przy użyciu [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
<a name="VSResFiles"></a>   
## <a name="resource-files-in-visual-studio"></a>Pliki zasobów w programie Visual Studio  
 Po dodaniu pliku zasobu do projektu programu Visual Studio, Visual Studio tworzy plik .resx w katalogu projektu. Program Visual Studio udostępnia edytory zasobów, które umożliwiają dodawanie ciągów, obrazy i obiektów binarnych. Ponieważ edytory są przeznaczone do obsługi tylko dane statyczne, nie można ich używać do przechowywania obiektów programowych; Musisz wpisywanie danych o obiektach do jednego pliku .resx lub do .resources plików programowo. Zobacz [Praca z programowo pliki resx](../../../docs/framework/resources/working-with-resx-files-programmatically.md) tematu i [zasobów plików .resources](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles) sekcji, aby uzyskać więcej informacji.  
  
 Jeśli dodajesz zlokalizowanych zasobów, należy przydzielić im taką samą nazwę pliku głównego jak plik zasobu głównego i należy wyznaczyć ich kultury w nazwie pliku. Na przykład jeśli dodasz plik zasobów o nazwie Resources.resx może także utworzyć pliki zasobów o nazwie Resources.en US.resx i Resources.fr FR.resx, aby pomieścić zlokalizowanych zasobów dla języka angielskiego (USA) i francuski (Francja) kultury, odpowiednio. Należy też określić kultury domyślnej aplikacji. Jest to kultura, do którego zasoby są używane w przypadku nieodnalezienia nie zlokalizowanych zasobów dla określonej kultury. Aby określić domyślną kulturę, w Eksploratorze rozwiązań w programie Visual Studio, kliknij prawym przyciskiem myszy nazwę projektu, wskaż polecenie aplikacji, kliknij polecenie **informacji o zestawie**i wybierz odpowiedni język/kultury w **Neutral język** listy.  
  
 W czasie kompilacji programu Visual Studio najpierw konwertuje pliki resx w projekcie pliki zasobów binarnych (.resources) i przechowuje je w podkatalogu w katalogu projektu. Visual Studio osadza pliki zasobów, które nie zawierają zlokalizowanych zasobów w zestawie głównym, który został wygenerowany przez projekt. Jeśli pliki zasobów zawiera zasoby zlokalizowane, Visual Studio umieszcza je w oddzielne zestawy satelickie dla każdego zlokalizowanych kultury. Następnie zapisuje każdego zestawu satelickiego w katalogu, którego nazwa odpowiada thelocalized kultury. Na przykład zlokalizowanych zasobów angielski (Stany Zjednoczone) są przechowywane w zestawie satelickim w podkatalogu en US.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Resources>  
 [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)  
 [Opakowanie i wdrażanie zasobów](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
