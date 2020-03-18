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
ms.openlocfilehash: 3b5a92948a3e692a734f3ddee3c7238d5d27588f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157055"
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a>Wskazówki: Tworzenie obiektów dynamicznych i posługiwanie się nimi (C# i Visual Basic)

Obiekty dynamiczne uwidaczniają elementy członkowskie, takie jak właściwości i metody w czasie wykonywania, a nie w czasie kompilacji. Dzięki temu można tworzyć obiekty do pracy ze strukturami, które nie pasują do typu statycznego lub formatu. Na przykład można użyć obiektu dynamicznego, aby odwołać się do modelu obiektu dokumentu HTML (DOM), który może zawierać dowolną kombinację prawidłowych elementów znaczników HTML i atrybutów. Ponieważ każdy dokument HTML jest unikatowy, członkowie określonego dokumentu HTML są określani w czasie wykonywania. Wspólną metodą odwoływania się do atrybutu elementu HTML jest `GetProperty` przekazanie nazwy atrybutu do metody elementu. Aby `id` odwołać się do `<div id="Div1">`atrybutu elementu HTML, `<div>` najpierw uzyskujesz odwołanie do elementu, a następnie użyj . `divElement.GetProperty("id")` Jeśli używasz obiektu dynamicznego, można `id` odwołać się do atrybutu jako `divElement.id`.  
  
 Obiekty dynamiczne zapewniają również wygodny dostęp do dynamicznych języków, takich jak IronPython i IronRuby. Obiekt dynamiczny służy do odwoływania się do skryptu dynamicznego, który jest interpretowany w czasie wykonywania.  
  
 Odwołujesz się do obiektu dynamicznego przy użyciu późnego wiązania. W języku C#typ obiektu z późnym `dynamic`wiązaniem określa się jako . W języku Visual Basic można określić typ `Object`obiektu z późnym wiązaniem jako . Aby uzyskać więcej informacji, zobacz [dynamiczne](../../language-reference/builtin-types/reference-types.md) i [wczesne i późne wiązanie](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
 Niestandardowe obiekty dynamiczne można tworzyć przy <xref:System.Dynamic?displayProperty=nameWithType> użyciu klas w obszarze nazw. Na przykład można utworzyć <xref:System.Dynamic.ExpandoObject> i określić elementy członkowskie tego obiektu w czasie wykonywania. Można również utworzyć własny typ, <xref:System.Dynamic.DynamicObject> który dziedziczy klasę. Następnie można zastąpić członków klasy, <xref:System.Dynamic.DynamicObject> aby zapewnić funkcje dynamiczne w czasie wykonywania.  
  
 W tym instruktazu można wykonać następujące zadania:  
  
- Utwórz obiekt niestandardowy, który dynamicznie udostępnia zawartość pliku tekstowego jako właściwości obiektu.  
  
- Utwórz projekt, `IronPython` który używa biblioteki.  
  
## <a name="prerequisites"></a>Wymagania wstępne  

Aby wypełnić ten instruktaż, musisz [ironpython](https://ironpython.net/) dla .NET. Przejdź do [strony pobierania,](https://ironpython.net/download/) aby uzyskać najnowszą wersję.
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-custom-dynamic-object"></a>Tworzenie niestandardowego obiektu dynamicznego

Pierwszy projekt utworzony w tym instruktacie definiuje niestandardowy obiekt dynamiczny, który przeszukuje zawartość pliku tekstowego. Tekst do wyszukania jest określony przez nazwę właściwości dynamicznej. Na przykład jeśli kod `dynamicFile.Sample`wywołujący określa , klasa dynamiczna zwraca ogólną listę ciągów, która zawiera wszystkie wiersze z pliku, który zaczyna się od "Przykład". W wyszukiwaniu nie uwzględnia się wielkości liter. Klasa dynamiczna obsługuje również dwa opcjonalne argumenty. Pierwszy argument jest wartością wyliczenia opcji wyszukiwania, która określa, że klasa dynamiczna powinna wyszukiwać dopasowania na początku wiersza, na końcu wiersza lub w dowolnym miejscu w wierszu. Drugi argument określa, że klasa dynamiczna powinna przyciąć spacje wiodące i końcowe z każdego wiersza przed wyszukiwaniem. Na przykład jeśli kod `dynamicFile.Sample(StringSearchOption.Contains)`wywołujący określa, klasa dynamiczna wyszukuje "Przykład" w dowolnym miejscu w wierszu. Jeśli kod wywołujący określa, klasa dynamiczna wyszukuje `dynamicFile.Sample(StringSearchOption.StartsWith, false)`"Przykład" na początku każdego wiersza i nie usuwa spacji wiodących i końcowych. Domyślnym zachowaniem klasy dynamicznej jest wyszukiwanie dopasowania na początku każdego wiersza i usuwanie spacji wiodących i końcowych.  
  
### <a name="to-create-a-custom-dynamic-class"></a>Aby utworzyć niestandardową klasę dynamiczną  
  
1. Uruchom program Visual Studio.  
  
2. W menu **Plik** wskaż polecenie **Nowy,** a następnie kliknij polecenie **Projekt**.  
  
3. W oknie dialogowym **Nowy projekt** w okienku **Typy projektów** upewnij się, że jest zaznaczona opcja **Windows.** Wybierz **pozycję Aplikacja konsoli** w okienku **Szablony.** W polu **Nazwa** `DynamicSample`wpisz , a następnie kliknij przycisk **OK**. Zostanie utworzony nowy projekt.  
  
4. Kliknij prawym przyciskiem myszy projekt DynamicSample i wskaż polecenie **Dodaj**, a następnie kliknij polecenie **Klasa**. W polu **Nazwa** `ReadOnlyFile`wpisz , a następnie kliknij przycisk **OK**. Nowy plik jest dodawany, który zawiera ReadOnlyFile klasy.  
  
5. U góry pliku ReadOnlyFile.cs lub ReadOnlyFile.vb dodaj następujący kod, aby zaimportować <xref:System.IO?displayProperty=nameWithType> obszary nazw i <xref:System.Dynamic?displayProperty=nameWithType> je.  

    [!code-csharp[VbDynamicWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#1)]
    [!code-vb[VbDynamicWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#1)]  

6. Niestandardowy obiekt dynamiczny używa wyliczenia do określenia kryteriów wyszukiwania. Przed class instrukcji, dodaj następującą definicję wyliczenia.  
  
    [!code-csharp[VbDynamicWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#2)]
    [!code-vb[VbDynamicWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#2)]
  
7. Zaktualizuj instrukcję klasy, aby odziedziczyć `DynamicObject` klasę, jak pokazano w poniższym przykładzie kodu.  
  
    [!code-csharp[VbDynamicWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#3)]
    [!code-vb[VbDynamicWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#3)]

8. Dodaj następujący kod `ReadOnlyFile` do klasy, aby zdefiniować pole prywatne dla ścieżki pliku i konstruktora dla `ReadOnlyFile` klasy.  
  
    [!code-csharp[VbDynamicWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#4)]
    [!code-vb[VbDynamicWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#4)]
  
9. Dodaj następującą metodę `GetPropertyValue` do klasy `ReadOnlyFile`. Metoda `GetPropertyValue` przyjmuje jako dane wejściowe kryteria wyszukiwania i zwraca wiersze z pliku tekstowego, który spełnia te kryteria wyszukiwania. Metody dynamiczne dostarczone przez `ReadOnlyFile` klasy `GetPropertyValue` wywołać metodę, aby pobrać ich odpowiednie wyniki.  
  
    [!code-csharp[VbDynamicWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#5)]
    [!code-vb[VbDynamicWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#5)]  
  
10. Po `GetPropertyValue` metody dodaj następujący kod, aby <xref:System.Dynamic.DynamicObject.TryGetMember%2A> zastąpić <xref:System.Dynamic.DynamicObject> metodę klasy. Metoda <xref:System.Dynamic.DynamicObject.TryGetMember%2A> jest wywoływana, gdy żądany jest element członkowski klasy dynamicznej i nie określono żadnych argumentów. Argument `binder` zawiera informacje o odwołuje się `result` element członkowski i argument odwołuje się do wyniku zwróconego dla określonego elementu członkowskiego. Metoda <xref:System.Dynamic.DynamicObject.TryGetMember%2A> zwraca wartość logiczną, `true` która zwraca, jeśli istnieje żądany element członkowski; w przeciwnym `false`razie zwraca .  
  
    [!code-csharp[VbDynamicWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#6)]
    [!code-vb[VbDynamicWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#6)]
  
11. Po `TryGetMember` metody dodaj następujący kod, aby <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> zastąpić <xref:System.Dynamic.DynamicObject> metodę klasy. Metoda <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> jest wywoływana, gdy element członkowski klasy dynamicznej jest wymagane z argumentami. Argument `binder` zawiera informacje o odwołuje się `result` element członkowski i argument odwołuje się do wyniku zwróconego dla określonego elementu członkowskiego. Argument `args` zawiera tablicę argumentów, które są przekazywane do elementu członkowskiego. Metoda <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> zwraca wartość logiczną, `true` która zwraca, jeśli istnieje żądany element członkowski; w przeciwnym `false`razie zwraca .  
  
    Niestandardowa wersja `TryInvokeMember` metody oczekuje, że pierwszy argument `StringSearchOption` będzie wartością z wyliczenia zdefiniowaną w poprzednim kroku. Metoda `TryInvokeMember` oczekuje, że drugi argument jest wartością logiczną. Jeśli jeden lub oba argumenty są prawidłowe `GetPropertyValue` wartości, są one przekazywane do metody, aby pobrać wyniki.  
  
    [!code-csharp[VbDynamicWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#7)]
    [!code-vb[VbDynamicWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#7)]
  
12. Zapisz i zamknij plik.  
  
#### <a name="to-create-a-sample-text-file"></a>Aby utworzyć przykładowy plik tekstowy  
  
1. Kliknij prawym przyciskiem myszy projekt DynamicSample i wskaż polecenie **Dodaj**, a następnie kliknij polecenie **Nowy element**. W okienku **Zainstalowane szablony** wybierz pozycję **Ogólne**, a następnie wybierz szablon **Plik tekstowy.** Pozostaw domyślną nazwę pliku TextFile1.txt w polu **Nazwa,** a następnie kliknij przycisk **Dodaj**. Nowy plik tekstowy zostanie dodany do projektu.  
  
2. Skopiuj następujący tekst do pliku TextFile1.txt.  
  
    ```text  
    List of customers and suppliers  
  
    Supplier: Lucerne Publishing (https://www.lucernepublishing.com/)  
    Customer: Preston, Chris  
    Customer: Hines, Patrick  
    Customer: Cameron, Maria  
    Supplier: Graphic Design Institute (https://www.graphicdesigninstitute.com/)
    Supplier: Fabrikam, Inc. (https://www.fabrikam.com/)
    Customer: Seubert, Roxanne  
    Supplier: Proseware, Inc. (http://www.proseware.com/)
    Customer: Adolphi, Stephan  
    Customer: Koch, Paul  
    ```  
  
3. Zapisz i zamknij plik.  
  
#### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a>Aby utworzyć przykładową aplikację, która używa niestandardowego obiektu dynamicznego  
  
1. W **Eksploratorze rozwiązań**kliknij dwukrotnie plik Module1.vb, jeśli używasz programu Visual Basic lub pliku Program.cs, jeśli używasz języka Visual C#.  
  
2. Dodaj poniższy kod do procedury Main, aby `ReadOnlyFile` utworzyć wystąpienie klasy dla pliku TextFile1.txt. Kod używa późnego wiązania do wywołania dynamicznych elementów członkowskich i pobierania wierszy tekstu, które zawierają ciąg "Klient".  
  
     [!code-csharp[VbDynamicWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/program.cs#8)]
     [!code-vb[VbDynamicWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/module1.vb#8)]
  
3. Zapisz plik i naciśnij klawisze CTRL+F5, aby utworzyć i uruchomić aplikację.  
  
## <a name="calling-a-dynamic-language-library"></a>Wywoływanie dynamicznej biblioteki językowej  

Następny projekt utworzony w tym instruktacie uzyskuje dostęp do biblioteki napisanej w języku dynamicznym IronPython.
  
### <a name="to-create-a-custom-dynamic-class"></a>Aby utworzyć niestandardową klasę dynamiczną
  
1. W programie Visual Studio w menu **Plik** wskaż polecenie **Nowy,** a następnie kliknij polecenie **Project**.  
  
2. W oknie dialogowym **Nowy projekt** w okienku **Typy projektów** upewnij się, że jest zaznaczona opcja **Windows.** Wybierz **pozycję Aplikacja konsoli** w okienku **Szablony.** W polu **Nazwa** `DynamicIronPythonSample`wpisz , a następnie kliknij przycisk **OK**. Zostanie utworzony nowy projekt.  
  
3. Jeśli używasz języka Visual Basic, kliknij prawym przyciskiem myszy projekt DynamicIronPythonSample, a następnie kliknij polecenie **Właściwości**. Kliknij kartę **Odwołania.** Kliknij przycisk **Dodaj.** Jeśli używasz programu Visual C#, w **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy folder **Odwołania,** a następnie kliknij polecenie **Dodaj odwołanie**.  
  
4. Na karcie **Przeglądaj** przejdź do folderu, w którym są zainstalowane biblioteki IronPython. Na przykład C:\Program Files\IronPython 2.6 dla .NET 4.0. Wybierz biblioteki **IronPython.dll**, **IronPython.Modules.dll**, **Microsoft.Scripting.dll**i **Microsoft.Dynamic.dll.** Kliknij przycisk **OK**.  
  
5. Jeśli używasz języka Visual Basic, zwyć plik Module1.vb. Jeśli używasz programu Visual C#, zamieł Program.cs pliku.  
  
6. U góry pliku dodaj następujący kod, aby `Microsoft.Scripting.Hosting` `IronPython.Hosting` zaimportować i przestrzenie nazw z bibliotek IronPython.  
  
    [!code-csharp[VbDynamicWalkthroughIronPython#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#1)]
    [!code-vb[VbDynamicWalkthroughIronPython#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#1)]
  
7. W Main metody dodaj następujący kod, `Microsoft.Scripting.Hosting.ScriptRuntime` aby utworzyć nowy obiekt do obsługi bibliotek IronPython. Obiekt `ScriptRuntime` ładuje moduł biblioteki IronPython random.py.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#2)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#2)]
  
8. Po załadowania modułu random.py należy dodać następujący kod, aby utworzyć tablicę liczb całkowitych. Tablica jest przekazywana `shuffle` do metody modułu random.py, który losowo sortuje wartości w tablicy.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#3)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#3)]
  
9. Zapisz plik i naciśnij klawisze CTRL+F5, aby utworzyć i uruchomić aplikację.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Dynamic?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [Używanie typu dynamicznego](./using-type-dynamic.md)
- [Wczesne i późne wiązanie](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [Dynamiczne](../../language-reference/builtin-types/reference-types.md)
- [Implementowanie interfejsów dynamicznych (plik PDF do pobrania z witryny Microsoft TechNet)](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)
