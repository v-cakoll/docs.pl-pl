---
title: 'Wskazówki: Tworzenie obiektów dynamicznych i posługiwanie się nimi (C# i Visual Basic)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dynamic objects [Visual Basic]
- dynamic objects
- dynamic objects [C#]
ms.assetid: 568f1645-1305-4906-8625-5d77af81e04f
ms.openlocfilehash: a04962912e3bc54d600b4514967cbc40a0d4f590
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420879"
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a>Wskazówki: Tworzenie obiektów dynamicznych i posługiwanie się nimi (C# i Visual Basic)

Obiekty dynamiczne udostępnianie składowych, takich jak właściwości i metody w czasie wykonywania, zamiast w w czasie kompilacji. Dzięki temu można utworzyć obiekty przeznaczone do pracy ze strukturami, które nie są zgodne, typu statycznego lub w formacie. Na przykład można użyć obiekt dynamiczny do odwołania HTML Document Object Model (DOM), który może zawierać dowolną kombinację prawidłowe elementów kodu znaczników HTML i atrybutów. Ponieważ każdy dokument HTML jest unikatowy, elementy członkowskie dla określonego dokumentu HTML są określane w czasie wykonywania. Częstą metodą można odwoływać się do atrybutu elementu HTML jest przekazanie nazwę atrybutu, aby `GetProperty` metoda elementu. Odwołania do `id` atrybutu elementu HTML `<div id="Div1">`, należy najpierw uzyskać odwołanie do `<div>` elementu, a następnie użyj `divElement.GetProperty("id")`. Jeśli używasz obiekt dynamiczny, można się odwołać `id` atrybutu jako `divElement.id`.  
  
 Obiekty dynamiczne również zapewniają wygodny dostęp do dynamicznego języków, takich jak IronPython i IronRuby. Obiekt dynamiczny służy do odwoływania się do dynamicznego skryptu, który jest interpretowany w czasie wykonywania.  
  
 Obiekt dynamiczny odwoływać się za pomocą późnego wiązania. W języku C#, określ typ obiektu z późnym wiązaniem jako `dynamic`. W języku Visual Basic określić typ obiektu z późnym wiązaniem jako `Object`. Aby uzyskać więcej informacji, zobacz [dynamiczne](../../../csharp/language-reference/keywords/dynamic.md) i [wczesnego a późne wiązanie](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
 Możesz tworzyć niestandardowe obiekty dynamiczne przy użyciu klas w <xref:System.Dynamic?displayProperty=nameWithType> przestrzeni nazw. Na przykład można utworzyć <xref:System.Dynamic.ExpandoObject> i określić elementy członkowskie tego obiektu w czasie wykonywania. Można również utworzyć swój własny typ, który dziedziczy <xref:System.Dynamic.DynamicObject> klasy. Następnie można zastąpić elementów członkowskich <xref:System.Dynamic.DynamicObject> klasy, które umożliwiają korzystanie z funkcji dynamicznych w czasie wykonywania.  
  
 W tym instruktażu wykonasz następujące zadania:  
  
-   Utwórz niestandardowy obiekt, który dynamicznie udostępnia zawartość pliku tekstowego jako właściwości obiektu.  
  
-   Utwórz projekt, który używa `IronPython` biblioteki.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
Potrzebujesz [IronPython](http://ironpython.net/) dla platformy .NET w celu przeprowadzenia tego instruktażu. Przejdź do ich [strony pobierania](http://ironpython.net/download/) uzyskanie najnowszej wersji.
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-custom-dynamic-object"></a>Tworzenie niestandardowych obiektów dynamicznych

Pierwszy projekt, który zostanie utworzony w tym przewodniku definiuje niestandardowy obiekt dynamiczny, który wyszukuje zawartość pliku tekstowego. Tekst do wyszukania jest określony przez nazwę właściwości dynamicznych. Na przykład, jeśli wywołanie kodu Określa `dynamicFile.Sample`, klasa dynamiczne zwraca ogólnego listę ciągów zawierającą wszystkie wiersze z pliku, które zaczynają się od "Przykładowy". Wyszukiwanie jest rozróżniana wielkość liter. Klasa dynamiczna obsługuje również dwa argumenty opcjonalne. Pierwszy argument jest wartość wyliczenia opcji wyszukiwania, określający klasy dynamicznej powinno poszukać dopasowań na początku wiersza, koniec wiersza i w dowolnym miejscu w wierszu. Drugi argument określa, czy klasy dynamicznej należy przyciąć spacje początkowe i końcowe z każdej linii przed wyszukiwaniem. Na przykład, jeśli wywołanie kodu Określa `dynamicFile.Sample(StringSearchOption.Contains)`, klasa dynamiczna wyszukuje "Przykładowy" dowolne miejsce w wierszu. Jeśli wywołanie kodu Określa `dynamicFile.Sample(StringSearchOption.StartsWith, false)`, klasa dynamiczna wyszukuje "Przykładowy" na początku każdego wiersza i nie powoduje usunięcia spacji wiodących i końcowych. Domyślne zachowanie klasy dynamicznych jest można wyszukiwać dopasowania na początku każdego wiersza i Usuń spacje początkowe i końcowe.  
  
### <a name="to-create-a-custom-dynamic-class"></a>Do tworzenia niestandardowych klas dynamicznych  
  
1.  Uruchom program Visual Studio.  
  
2.  Na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.  
  
3.  W **nowy projekt** dialogowym **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone. Wybierz **aplikację Konsolową** w **szablony** okienka. W **nazwa** wpisz `DynamicSample`, a następnie kliknij przycisk **OK**. Nowy projekt zostanie utworzony.  
  
4.  Kliknij prawym przyciskiem myszy projekt DynamicSample, a następnie wskaż **Dodaj**, a następnie kliknij przycisk **klasy**. W **nazwa** wpisz `ReadOnlyFile`, a następnie kliknij przycisk **OK**. Nowy plik zostanie dodany, który zawiera klasę ReadOnlyFile.  
  
5.  W górnej części pliku ReadOnlyFile.cs lub ReadOnlyFile.vb, Dodaj następujący kod umożliwiający zaimportowanie <xref:System.IO?displayProperty=nameWithType> i <xref:System.Dynamic?displayProperty=nameWithType> przestrzeni nazw.  

    [!code-csharp[VbDynamicWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#1)]
    [!code-vb[VbDynamicWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#1)]  

6.  Niestandardowy obiekt dynamiczny używa wyliczeniem, aby określić kryteria wyszukiwania. Przed instrukcją klasy Dodaj następującą definicję typu wyliczeniowego.  
  
    [!code-csharp[VbDynamicWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#2)]
    [!code-vb[VbDynamicWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#2)]
  
7.  Aktualizuj class — instrukcja w celu odziedziczenia `DynamicObject` klasy, jak pokazano w poniższym przykładzie kodu.  
  
    [!code-csharp[VbDynamicWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#3)]
    [!code-vb[VbDynamicWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#3)]

8.  Dodaj następujący kod do `ReadOnlyFile` klasy, aby zdefiniować pole prywatne dla ścieżki pliku i Konstruktor dla `ReadOnlyFile` klasy.  
  
    [!code-csharp[VbDynamicWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#4)]
    [!code-vb[VbDynamicWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#4)]
  
9. Dodaj następujący kod `GetPropertyValue` metody `ReadOnlyFile` klasy. `GetPropertyValue` Metoda przyjmuje jako dane wejściowe, kryteriów wyszukiwania i zwraca wiersze z pliku tekstowego plików spełniających i kryteria wyszukiwania. Dynamiczne metod dostarczonych przez `ReadOnlyFile` klasy wywołania `GetPropertyValue` metoda pobierania ich odpowiednich wyników.  
  
    [!code-csharp[VbDynamicWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#5)]
    [!code-vb[VbDynamicWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#5)]  
  
10. Po `GetPropertyValue` metody, Dodaj następujący kod, aby zastąpić <xref:System.Dynamic.DynamicObject.TryGetMember%2A> metody <xref:System.Dynamic.DynamicObject> klasy. <xref:System.Dynamic.DynamicObject.TryGetMember%2A> Metoda jest wywoływana, gdy członek klasy dynamicznej zostanie zażądany nie podano argumentów. `binder` Argument zawiera informacje o przywoływanego elementu członkowskiego, a `result` argument odwołuje się do wyniku zwrócony dla określonego elementu członkowskiego. <xref:System.Dynamic.DynamicObject.TryGetMember%2A> Metoda zwraca wartość logiczną, która zwraca `true` Jeśli wymagany element istnieje; w przeciwnym razie zwraca `false`.  
  
    [!code-csharp[VbDynamicWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#6)]
    [!code-vb[VbDynamicWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#6)]
  
11. Po `TryGetMember` metody, Dodaj następujący kod, aby zastąpić <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> metody <xref:System.Dynamic.DynamicObject> klasy. <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> Metoda jest wywoływana, gdy zażądano składową klasy dynamicznej z argumentami. `binder` Argument zawiera informacje o przywoływanego elementu członkowskiego, a `result` argument odwołuje się do wyniku zwrócony dla określonego elementu członkowskiego. `args` Argument zawiera tablicę argumentów, które są przekazywane do elementu członkowskiego. <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> Metoda zwraca wartość logiczną, która zwraca `true` Jeśli wymagany element istnieje; w przeciwnym razie zwraca `false`.  
  
    Niestandardową wersję `TryInvokeMember` metoda oczekuje pierwszy argument jako wartość z zakresu od `StringSearchOption` wyliczenia, które są zdefiniowane w poprzednim kroku. `TryInvokeMember` Metoda oczekuje, że drugi argument typu wartość logiczna. Jeśli jeden lub oba argumenty mają prawidłowe wartości, są przekazywane do `GetPropertyValue` metody do pobierania wyników.  
  
    [!code-csharp[VbDynamicWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#7)]
    [!code-vb[VbDynamicWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#7)]
  
12. Zapisz i zamknij plik.  
  
#### <a name="to-create-a-sample-text-file"></a>Aby utworzyć przykładowy plik tekstowy  
  
1.  Kliknij prawym przyciskiem myszy projekt DynamicSample, a następnie wskaż **Dodaj**, a następnie kliknij przycisk **nowy element**. W **zainstalowane szablony** okienku wybierz **ogólne**, a następnie wybierz pozycję **plik tekstowy** szablonu. Pozostaw domyślną nazwę TextFile1.txt w **nazwa** , a następnie kliknij przycisk **Dodaj**. Nowy plik tekstowy zostanie dodany do projektu.  
  
2.  Skopiuj poniższy tekst do pliku TextFile1.txt.  
  
    ```  
    List of customers and suppliers  
  
    Supplier: Lucerne Publishing (http://www.lucernepublishing.com/)  
    Customer: Preston, Chris  
    Customer: Hines, Patrick  
    Customer: Cameron, Maria  
    Supplier: Graphic Design Institute (http://www.graphicdesigninstitute.com/)   
    Supplier: Fabrikam, Inc. (http://www.fabrikam.com/)   
    Customer: Seubert, Roxanne  
    Supplier: Proseware, Inc. (http://www.proseware.com/)   
    Customer: Adolphi, Stephan  
    Customer: Koch, Paul  
    ```  
  
3.  Zapisz i zamknij plik.  
  
#### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a>Do tworzenia przykładowej aplikacji, która używa niestandardowych obiekt dynamiczny  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie plik Module1.vb, jeśli używasz języka Visual Basic lub pliku Program.cs Jeśli używasz Visual C#.  
  
2.  Dodaj następujący kod do procedurę Main, aby utworzyć wystąpienie `ReadOnlyFile` klasy dla pliku TextFile1.txt. Kod używa późne powiązania w celu wywołania dynamicznych elementów członkowskich i pobieranie wierszy tekstu, zawierających ciąg "Klient".  
  
     [!code-csharp[VbDynamicWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/program.cs#8)]
     [!code-vb[VbDynamicWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/module1.vb#8)]
  
3.  Zapisz plik, a następnie naciśnij klawisz CTRL + F5, aby skompilować i uruchomić aplikację.  
  
## <a name="calling-a-dynamic-language-library"></a>Podczas wywoływania biblioteki języka dynamicznego  

Podczas następnego projektu, który zostanie utworzony w tym przewodniku uzyskuje dostęp do biblioteki, która jest napisany w języku dynamiczne Ironpythonu.
  
### <a name="to-create-a-custom-dynamic-class"></a>Do tworzenia niestandardowych klas dynamicznych
  
1.  W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** dialogowym **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone. Wybierz **aplikację Konsolową** w **szablony** okienka. W **nazwa** wpisz `DynamicIronPythonSample`, a następnie kliknij przycisk **OK**. Nowy projekt zostanie utworzony.  
  
3.  Jeśli używasz języka Visual Basic, kliknij prawym przyciskiem myszy projekt DynamicIronPythonSample, a następnie kliknij przycisk **właściwości**. Kliknij przycisk **odwołania** kartę. Kliknij przycisk **Dodaj** przycisku. Jeśli używasz języka Visual C# w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** folder, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
4.  Na **Przeglądaj** karcie, przejdź do folderu, w którym są zainstalowane biblioteki Ironpythonu. Na przykład C:\Program Files\IronPython 2.6 dla platformy .NET 4.0. Wybierz **IronPython.dll**, **IronPython.Modules.dll**, **Microsoft.Scripting.dll**, i **Microsoft.Dynamic.dll** biblioteki . Kliknij przycisk **OK**.  
  
5.  Jeśli używasz języka Visual Basic, należy edytować plik Module1.vb. Jeśli używasz Visual C#, przeprowadź edycję pliku Program.cs.  
  
6.  W górnej części pliku Dodaj następujący kod umożliwiający zaimportowanie `Microsoft.Scripting.Hosting` i `IronPython.Hosting` przestrzenie nazw z bibliotek Ironpythonu.  
  
    [!code-csharp[VbDynamicWalkthroughIronPython#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#1)]
    [!code-vb[VbDynamicWalkthroughIronPython#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#1)]
  
7.  W przypadku metody Main, Dodaj następujący kod, aby utworzyć nową `Microsoft.Scripting.Hosting.ScriptRuntime` obiektu do obsługi bibliotek Ironpythonu. `ScriptRuntime` Obiektu ładuje random.py modułu biblioteki Ironpythonu.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#2)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#2)]
  
8.  Po kodzie, który można załadować modułu random.py Dodaj następujący kod, aby utworzyć tablicę wartości całkowitych. Tablica jest przekazywany do `shuffle` metoda moduł random.py, który losowo sortuje wartości w tablicy.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#3)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#3)]
  
9. Zapisz plik, a następnie naciśnij klawisz CTRL + F5, aby skompilować i uruchomić aplikację.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Dynamic?displayProperty=nameWithType>  
 <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>  
 [Używanie typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [Wczesne i późne powiązania](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
 [Implementowanie dynamicznych interfejsów (PDF do pobrania w witrynie Microsoft TechNet.)](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)
