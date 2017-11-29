---
title: "Wskazówki: Tworzenie obiektów dynamicznych i posługiwanie się nimi (C# i Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dynamic objects [Visual Basic]
- dynamic objects
- dynamic objects [C#]
ms.assetid: 568f1645-1305-4906-8625-5d77af81e04f
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab1e245ed806cf0ea6346c76c6ade83273eed7be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a>Wskazówki: Tworzenie obiektów dynamicznych i posługiwanie się nimi (C# i Visual Basic)

Obiekty dynamiczne udostępnić elementy członkowskie, takie jak właściwości i metody w czasie wykonywania, a nie w w czasie kompilacji. Pozwala na tworzenie obiektów do pracy z struktury, która nie pasuje do statycznego typ lub format. Na przykład można obiekt dynamiczny HTML modelu DOM (Document Object), który może zawierać dowolną kombinację prawidłowe elementy kodu znaczników HTML i atrybutów odwołania. Ponieważ każdy dokument HTML jest unikatowa, elementy członkowskie dla określonego dokumentu HTML są określane w czasie wykonywania. Częstą metodą aby odwoływać się do atrybutu HTML element jest przekazanie nazwa atrybutu, aby `GetProperty` metody elementu. Odwołania do `id` atrybut elementu HTML `<div id="Div1">`, należy najpierw uzyskać odwołanie do `<div>` elementu, a następnie użyć `divElement.GetProperty("id")`. Jeśli używasz obiekt dynamiczny, można odwoływać się `id` atrybutu jako `divElement.id`.  
  
 Obiekty dynamiczne również zapewniają wygodne dostęp do dynamicznego języków, takich jak IronPython i IronRuby. Obiekt dynamiczny służy do odwoływania się do dynamicznego skrypt, który jest interpretowany w czasie wykonywania.  
  
 Obiekt dynamiczny odwoływać się przy użyciu późnego wiązania. W języku C#, określ typ obiektu późnym wiązaniem jako `dynamic`. W [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], określ typ obiektu późnym wiązaniem jako `Object`. Aby uzyskać więcej informacji, zobacz [dynamiczne](../../../csharp/language-reference/keywords/dynamic.md) i [wczesnego i późne wiązanie](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
 Niestandardowe obiekty dynamiczne można tworzyć przy użyciu klasy w <xref:System.Dynamic?displayProperty=nameWithType> przestrzeni nazw. Na przykład można utworzyć <xref:System.Dynamic.ExpandoObject> i określ elementy członkowskie tego obiektu w czasie wykonywania. Można również tworzyć własne typ, który dziedziczy <xref:System.Dynamic.DynamicObject> klasy. Następnie można zastąpić elementów członkowskich <xref:System.Dynamic.DynamicObject> klasę, aby umożliwić korzystanie z funkcji dynamicznego środowiska wykonawczego.  
  
 W ramach tego przewodnika, wykonasz następujące zadania:  
  
-   Tworzenie niestandardowego obiektu, który dynamicznie udostępnia zawartość pliku tekstowego jako właściwości obiektu.  
  
-   Tworzenie projektu, który używa `IronPython` biblioteki.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
Należy [IronPython](http://ironpython.net/) dla platformy .NET, w tym przewodniku. Przejdź do ich [stronę pobierania](http://ironpython.net/download/) Aby uzyskać najnowszą wersję.
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-custom-dynamic-object"></a>Tworzenie niestandardowego obiektu dynamicznego  
 Pierwszy projekt, który można utworzyć w tym przewodniku definiuje obiekt dynamiczny niestandardowych przeszukuje zawartość pliku tekstowego. Tekst do wyszukania jest określony przez nazwę właściwości dynamicznych. Na przykład, jeśli wywołanie kodu Określa `dynamicFile.Sample`, klasy dynamicznej zwraca ogólnego listę ciągów zawierającą wszystkie wiersze z pliku, które zaczynają się od "Test". Wyszukiwanie jest rozróżniana wielkość liter. Klasa dynamiczna obsługuje również dwa argumenty opcjonalne. Pierwszy argument jest wartość enum opcji wyszukiwania, która określa, klasa dynamiczna ma poszukiwać dopasowuje początek linii końcu wiersza lub dowolne miejsce w wierszu. Drugi argument określa, czy dynamiczne klasy należy przyciąć spacje początkowe i końcowe z każdej linii przed wyszukiwaniem. Na przykład, jeśli wywołanie kodu Określa `dynamicFile.Sample(StringSearchOption.Contains)`, klasa dynamiczna wyszukuje "Test" dowolne miejsce w wierszu. Określa, czy wywołanie kodu `dynamicFile.Sample(StringSearchOption.StartsWith, false)`, klasa dynamiczna wyszukuje "Test" na początku każdego wiersza, a nie usuwa spacje początkowe i końcowe. Domyślne zachowanie klasy dynamicznej jest można wyszukiwać dopasowania na początku każdego wiersza i Usuń spacje początkowe i końcowe.  
  
#### <a name="to-create-a-custom-dynamic-class"></a>Aby utworzyć niestandardowe klasy dynamicznej  
  
1.  Uruchom [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].  
  
2.  Na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.  
  
3.  W **nowy projekt** okna dialogowego, **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone. Wybierz **aplikacji konsoli** w **szablony** okienka. W **nazwa** wpisz `DynamicSample`, a następnie kliknij przycisk **OK**. Nowy projekt zostanie utworzony.  
  
4.  Kliknij prawym przyciskiem myszy projekt DynamicSample, a następnie wskaż **Dodaj**, a następnie kliknij przycisk **klasy**. W **nazwa** wpisz `ReadOnlyFile`, a następnie kliknij przycisk **OK**. Zawiera klasy ReadOnlyFile jest dodać nowy plik.  
  
5.  W górnej części pliku ReadOnlyFile.cs lub ReadOnlyFile.vb, Dodaj następujący kod, aby zaimportować <xref:System.IO?displayProperty=nameWithType> i <xref:System.Dynamic?displayProperty=nameWithType> przestrzeni nazw.  
  
     [!code-csharp[VbDynamicWalkthrough#1](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_1.cs)]

     [!code-vb[VbDynamicWalkthrough#1](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_1.vb)]  
  
6.  Niestandardowego obiektu dynamicznego używa wyliczenia, aby określić kryteria wyszukiwania. Przed instrukcją klasy Dodaj następującą definicję wyliczenia.  
  
     [!code-csharp[VbDynamicWalkthrough#2](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_2.cs)]

     [!code-vb[VbDynamicWalkthrough#2](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_2.vb)]  
  
7.  Aktualizacja instrukcji klasa dziedziczy `DynamicObject` klasy, jak pokazano w poniższym przykładzie kodu.  
  
     [!code-csharp[VbDynamicWalkthrough#3](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_3.cs)]

     [!code-vb[VbDynamicWalkthrough#3](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_3.vb)]  
  
8.  Dodaj następujący kod do `ReadOnlyFile` zdefiniuj pole prywatne dla ścieżki pliku oraz Konstruktor dla klasy `ReadOnlyFile` klasy.  
  
     [!code-csharp[VbDynamicWalkthrough#4](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_4.cs)]
     
     [!code-vb[VbDynamicWalkthrough#4](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_4.vb)]  
  
9. Dodaj następujące `GetPropertyValue` metody `ReadOnlyFile` klasy. `GetPropertyValue` Metoda przyjmuje jako dane wejściowe, kryteria wyszukiwania i zwraca wiersze z tekstu plików pasujących kryteria wyszukiwania. Metody dynamiczne dostarczonych przez `ReadOnlyFile` klasy wywołania `GetPropertyValue` metoda pobierania ich odpowiednich wyników.  
  
     [!code-csharp[VbDynamicWalkthrough#5](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_5.cs)]
     
     [!code-vb[VbDynamicWalkthrough#5](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_5.vb)]  
  
10. Po `GetPropertyValue` metody, Dodaj następujący kod, aby zastąpić <xref:System.Dynamic.DynamicObject.TryGetMember%2A> metody <xref:System.Dynamic.DynamicObject> klasy. <xref:System.Dynamic.DynamicObject.TryGetMember%2A> Metoda jest wywoływana, gdy wymagany jest element członkowski klasy dynamicznej, a nie podano argumentów. `binder` Argument zawiera informacje o przywoływanego elementu członkowskiego i `result` argument odwołuje się do wyniku zwracanego dla określonego elementu członkowskiego. <xref:System.Dynamic.DynamicObject.TryGetMember%2A> Metoda zwraca wartość logiczną, która zwraca `true` przypadku żądanego członka istnieje; w przeciwnym razie zwraca `false`.  
  
     [!code-csharp[VbDynamicWalkthrough#6](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_6.cs)]
     
     [!code-vb[VbDynamicWalkthrough#6](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_6.vb)]  
  
11. Po `TryGetMember` metody, Dodaj następujący kod, aby zastąpić <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> metody <xref:System.Dynamic.DynamicObject> klasy. <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> Metoda jest wywoływana, gdy wymagane jest elementem członkowskim klasy dynamicznej z argumentami. `binder` Argument zawiera informacje o przywoływanego elementu członkowskiego i `result` argument odwołuje się do wyniku zwracanego dla określonego elementu członkowskiego. `args` Argument zawiera tablicę argumentów, które są przekazywane do elementu członkowskiego. <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> Metoda zwraca wartość logiczną, która zwraca `true` przypadku żądanego członka istnieje; w przeciwnym razie zwraca `false`.  
  
     Niestandardową wersję `TryInvokeMember` metoda oczekuje pierwszy argument jako wartość z zakresu od `StringSearchOption` wyliczenia, który został zdefiniowany w poprzednim kroku. `TryInvokeMember` Metoda oczekuje drugi argument jako wartość logiczną. Jeśli jeden lub oba argumenty mają prawidłowe wartości, są przekazywane do `GetPropertyValue` metoda pobierania wyników.  
  
     [!code-csharp[VbDynamicWalkthrough#7](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_7.cs)]
     
     [!code-vb[VbDynamicWalkthrough#7](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_7.vb)]  
  
12. Zapisz i zamknij plik.  
  
#### <a name="to-create-a-sample-text-file"></a>Aby utworzyć przykładowy plik tekstowy  
  
1.  Kliknij prawym przyciskiem myszy projekt DynamicSample, a następnie wskaż **Dodaj**, a następnie kliknij przycisk **nowy element**. W **zainstalowane szablony** okienku wybierz **ogólne**, a następnie wybierz **pliku tekstowego** szablonu. Pozostaw nazwę domyślną TextFile1.txt w **nazwa** , a następnie kliknij przycisk **Dodaj**. Nowy plik tekstowy jest dodane do projektu.  
  
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
  
#### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a>Do tworzenia przykładowej aplikacji, która używa niestandardowych obiektów dynamicznych  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie plik Module1.vb, jeśli używasz [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] lub plik Program.cs, jeśli używasz programu Visual C#.  
  
2.  Dodaj następujący kod do procedury główne utworzenia wystąpienia `ReadOnlyFile` klasy dla pliku TextFile1.txt. W kodzie użyto późne wiązanie wywołań dynamicznych elementów członkowskich i pobierania wierszy tekstu, zawierających ciąg "Klient".  
  
     [!code-csharp[VbDynamicWalkthrough#8](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_8.cs)]
     
     [!code-vb[VbDynamicWalkthrough#8](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_8.vb)]  
  
3.  Zapisz plik i naciśnij klawisze CTRL + F5, aby skompilować i uruchomić aplikację.  
  
## <a name="calling-a-dynamic-language-library"></a>Podczas wywoływania biblioteki języka dynamicznego  

Projekt dalej utworzonego w ramach tego przewodnika uzyskuje dostęp do biblioteki, która jest napisany w języku dynamiczne IronPython.
  
#### <a name="to-create-a-custom-dynamic-class"></a>Aby utworzyć niestandardowe klasy dynamicznej  
  
1.  W [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** okna dialogowego, **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone. Wybierz **aplikacji konsoli** w **szablony** okienka. W **nazwa** wpisz `DynamicIronPythonSample`, a następnie kliknij przycisk **OK**. Nowy projekt zostanie utworzony.  
  
3.  Jeśli używasz [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], kliknij prawym przyciskiem myszy projekt DynamicIronPythonSample, a następnie kliknij przycisk **właściwości**. Kliknij przycisk **odwołania** kartę. Kliknij przycisk **Dodaj** przycisku. Jeśli używasz programu Visual C# w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** folder, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
4.  Na **Przeglądaj** karcie, przejdź do folderu, w którym są zainstalowane w bibliotekach IronPython. Na przykład C:\Program Files\IronPython 2.6 dla programu .NET 4.0. Wybierz **IronPython.dll**, **IronPython.Modules.dll**, **Microsoft.Scripting.dll**, i **Microsoft.Dynamic.dll** biblioteki . Kliknij przycisk **OK**.  
  
5.  Jeśli używasz [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], przeprowadź edycję pliku Module1.vb. Jeśli używasz programu Visual C#, przeprowadź edycję pliku Program.cs.  
  
6.  W górnej części pliku, Dodaj następujący kod, aby zaimportować `Microsoft.Scripting.Hosting` i `IronPython.Hosting` przestrzeni nazw z bibliotek IronPython.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#1](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_9.cs)]
     
     [!code-vb[VbDynamicWalkthroughIronPython#1](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_9.vb)]  
  
7.  Metody Main, Dodaj następujący kod, aby utworzyć nową `Microsoft.Scripting.Hosting.ScriptRuntime` obiektu do biblioteki IronPython hosta. `ScriptRuntime` Random.py modułu biblioteki IronPython ładuje obiektu.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#2](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_10.cs)]
     
     [!code-vb[VbDynamicWalkthroughIronPython#2](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_10.vb)]  
  
8.  Po kodzie można załadować modułu random.py Dodaj następujący kod do utworzenia tablicy liczb całkowitych. Tablica jest przekazywana do `shuffle` metody module random.py losowo sortuje wartości w tablicy.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#3](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_11.cs)]
     
     [!code-vb[VbDynamicWalkthroughIronPython#3](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_11.vb)]  
  
9. Zapisz plik i naciśnij klawisze CTRL + F5, aby skompilować i uruchomić aplikację.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Dynamic?displayProperty=nameWithType>  
 <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>  
 [Używanie typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [Wczesne i późne powiązania](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [dynamiczne](../../../csharp/language-reference/keywords/dynamic.md)  
 [Implementowanie interfejsów dynamicznego (blog zewnętrznych)](http://go.microsoft.com/fwlink/?LinkId=230895)
