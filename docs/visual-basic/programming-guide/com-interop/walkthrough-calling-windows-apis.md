---
title: 'Przewodnik: Wywoływanie interfejsów API systemu Windows (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- DLLs, calling
- Windows API, walkthroughs
- platform invoke, walkthroughs
- API calls [Visual Basic], walkthroughs [Visual Basic]
- Windows API, calling
- walkthroughs [Visual Basic], API calls
- DllImport attribute, calling Windows API
- Declare statement [Visual Basic], declaring DLL functions
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
ms.openlocfilehash: 8e6d3e7f84c96d145a48daa27918cbb2cb3b61ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958308"
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>Przewodnik: Wywoływanie interfejsów API systemu Windows (Visual Basic)
Interfejsy API systemu Windows to biblioteki dołączane dynamicznie (dll), które są częścią systemu operacyjnego Windows. Są one używane do wykonywania zadań, gdy trudno jest pisać równoważne procedury. Na przykład system Windows udostępnia funkcję o nazwie `FlashWindowEx` , która umożliwia zmianę paska tytułu aplikacji między jasnym i ciemnym cieniami.  
  
 Zalety używania interfejsów API systemu Windows w kodzie polega na tym, że mogą one zaoszczędzić czas opracowywania, ponieważ zawierają dziesiątki użytecznych funkcji, które są już zapisane i oczekują na użycie. Wadą jest to, że interfejsy API systemu Windows mogą być trudne do pracy z i Unforgiving, gdy coś się nie stało.  
  
 Interfejsy API systemu Windows reprezentują specjalną kategorię współdziałania. Interfejsy API systemu Windows nie korzystają z kodu zarządzanego, nie mają wbudowanych bibliotek typów i używają typów danych, które są inne niż używane w programie Visual Studio. Ze względu na te różnice, ponieważ interfejsy API systemu Windows nie są obiektami COM, współdziałanie z interfejsami API systemu Windows i .NET Framework odbywa się przy użyciu funkcji Invoke platformy lub PInvoke. Wywołanie platformy to usługa, która umożliwia kodowi zarządzanemu wywoływanie funkcji niezarządzanych wdrożonych w bibliotekach DLL. Aby uzyskać więcej informacji, zobacz wykorzystywanie [niezarządzanych funkcji DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md). Możesz użyć funkcji PInvoke w Visual Basic, używając `Declare` instrukcji lub `DllImport` stosując atrybut do pustej procedury.  
  
 Wywołania interfejsu API systemu Windows były istotną częścią programowania Visual Basic w przeszłości, ale rzadko są konieczne w przypadku Visual Basic .NET. Jeśli to możliwe, należy używać kodu zarządzanego z .NET Framework do wykonywania zadań, zamiast wywołań interfejsu API systemu Windows. Ten Instruktaż zawiera informacje dotyczące tych sytuacji, w których jest wymagane korzystanie z interfejsów API systemu Windows.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>Wywołania interfejsu API za pomocą deklaracji DECLARE  
 Najbardziej typowym sposobem wywołania interfejsów API systemu Windows jest użycie `Declare` instrukcji.  
  
### <a name="to-declare-a-dll-procedure"></a>Aby zadeklarować procedurę DLL  
  
1. Określ nazwę funkcji, która ma zostać wywołana, oraz jej argumenty, typy argumentów i wartość zwracaną, a także nazwę i lokalizację biblioteki DLL, która ją zawiera.  
  
    > [!NOTE]
    > Aby uzyskać pełne informacje na temat interfejsów API systemu Windows, zobacz dokumentację zestawu Win32 SDK w interfejsie API systemu Windows zestawu SDK platformy. Aby uzyskać więcej informacji na temat stałych używanych przez interfejsy API systemu Windows, należy przejrzeć pliki nagłówkowe, takie jak Windows. h, dołączone do zestawu SDK platformy.  
  
2. Otwórz nowy projekt aplikacji systemu Windows, klikając pozycję **Nowy** w menu **plik** , a następnie klikając pozycję **projekt**. **Nowy projekt** pojawi się okno dialogowe.  
  
3. Wybierz pozycję **aplikacja systemu Windows** z listy Visual Basic szablonów projektu. Zostanie wyświetlony nowy projekt.  
  
4. Dodaj następującą `Declare` funkcję do klasy lub modułu, w którym ma być używana biblioteka DLL:  
  
     [!code-vb[VbVbalrInterop#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#9)]  
  
### <a name="parts-of-the-declare-statement"></a>Części instrukcji DECLARE  
 `Declare` Instrukcja zawiera następujące elementy.  
  
#### <a name="auto-modifier"></a>Modyfikator Autokorekty  
 `Auto` Modyfikator instruuje środowisko uruchomieniowe, aby przekonwertował ciąg na podstawie nazwy metody zgodnie z regułami środowiska uruchomieniowego języka wspólnego (lub nazwą aliasu, jeśli jest określona).  
  
#### <a name="lib-and-alias-keywords"></a>Lib i słowa kluczowe aliasu  
 Nazwa po `Function` słowie kluczowym jest nazwą używaną przez program w celu uzyskania dostępu do zaimportowanej funkcji. Może być taka sama jak prawdziwa nazwa wywoływanej funkcji lub można użyć dowolnej prawidłowej nazwy procedury, a następnie zastosować `Alias` słowo kluczowe, aby określić rzeczywistą nazwę wywoływanej funkcji.  
  
 `Lib` Określ słowo kluczowe, a następnie nazwę i lokalizację biblioteki DLL zawierającej wywoływaną funkcję. Nie trzeba określać ścieżki dla plików znajdujących się w katalogach systemu Windows.  
  
 `Alias` Użyj słowa kluczowego, jeśli nazwa wywoływanej funkcji nie jest prawidłową nazwą procedury Visual Basic lub powoduje konflikt z nazwą innych elementów w aplikacji. `Alias`wskazuje rzeczywistą nazwę wywoływanej funkcji.  
  
#### <a name="argument-and-data-type-declarations"></a>Deklaracje typu argumentu i danych  
 Zadeklaruj argumenty i ich typy danych. Ta część może być trudne, ponieważ typy danych używane przez system Windows nie odpowiadają typom danych programu Visual Studio. Visual Basic wykonuje dużą część pracy przez konwersję argumentów na zgodne typy danych, proces o nazwie Marshaling. Można jawnie kontrolować sposób, w jaki argumenty są organizowane przy użyciu <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu zdefiniowanego <xref:System.Runtime.InteropServices> w przestrzeni nazw.  
  
> [!NOTE]
> Poprzednie wersje Visual Basic mogły zadeklarować parametry `As Any`, co oznacza, że można użyć danych dowolnego typu danych. Visual Basic wymaga użycia określonego typu danych dla wszystkich `Declare` instrukcji.  
  
#### <a name="windows-api-constants"></a>Stałe interfejsu API systemu Windows  
 Niektóre argumenty są kombinacją stałych. Na przykład `MessageBox` interfejs API przedstawiony w tym instruktażu akceptuje argument liczby całkowitej o `Typ` nazwie, który kontroluje sposób wyświetlania okna komunikatu. Możesz określić wartość liczbową tych stałych, sprawdzając `#define` instrukcje w pliku Winuser. h. Wartości liczbowe są zwykle wyświetlane w formacie szesnastkowym, więc możesz chcieć użyć kalkulatora, aby dodać je i przekonwertować na wartość typu Decimal. Na przykład, jeśli chcesz połączyć stałe dla 0x00000030 stylu `MB_ICONEXCLAMATION` wykrzyknika i tak/bez stylu `MB_YESNO` 0x00000004, można dodać liczby i uzyskać wynik 0x00000034 lub 52 dziesiętnych. Mimo że można użyć bezpośredniego wyniku dziesiętnego, lepiej jest zadeklarować te wartości jako stałe w aplikacji i połączyć je za pomocą `Or` operatora.  
  
##### <a name="to-declare-constants-for-windows-api-calls"></a>Aby zadeklarować stałe dla wywołań interfejsu API systemu Windows  
  
1. Zapoznaj się z dokumentacją dla wywoływanej funkcji systemu Windows. Określ nazwę stałych, z których korzysta, i nazwę pliku h, który zawiera wartości liczbowe dla tych stałych.  
  
2. Użyj edytora tekstu, takiego jak Notatnik, aby wyświetlić zawartość pliku nagłówkowego (. h) i znaleźć wartości skojarzone z używanymi przez Ciebie stałych. Na przykład `MessageBox` interfejs API używa stałej `MB_ICONQUESTION` do wyświetlania znaku zapytania w oknie komunikatu. Definicja programu `MB_ICONQUESTION` jest w Winuser. h i wygląda następująco:  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3. Dodaj równoważne `Const` instrukcje do klasy lub modułu, aby udostępnić te stałe aplikacji. Przykład:  
  
     [!code-vb[VbVbalrInterop#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#11)]  
  
###### <a name="to-call-the-dll-procedure"></a>Aby wywołać procedurę DLL  
  
1. Dodaj przycisk o nazwie `Button1` do formularza startowego dla projektu, a następnie kliknij go dwukrotnie, aby wyświetlić jego kod. Zostanie wyświetlony program obsługi zdarzeń dla przycisku.  
  
2. Dodaj kod do `Click` programu obsługi zdarzeń dla przycisku, który został dodany, aby wywołać procedurę i podać odpowiednie argumenty:  
  
     [!code-vb[VbVbalrInterop#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#12)]  
  
3. Uruchom projekt, naciskając klawisz F5. Zostanie wyświetlone okno komunikatu z przyciskami **tak** i **bez** odpowiedzi. Kliknij jeden z nich.  
  
#### <a name="data-marshaling"></a>Kierowanie danych  
 Visual Basic automatycznie konwertuje typy danych parametrów i wartości zwracane dla wywołań interfejsu API systemu Windows, ale można użyć `MarshalAs` atrybutu, aby jawnie określić niezarządzane typy danych, których oczekuje interfejs API. Aby uzyskać więcej informacji na temat organizowania międzyoperacyjności, zobacz [organizowanie](../../../framework/interop/interop-marshaling.md)międzyoperacyjnych.  
  
##### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>Aby użyć DECLARE i MarshalAs w wywołaniu interfejsu API  
  
1. Określ nazwę funkcji, którą chcesz wywołać, oraz jej argumenty, typy danych i wartość zwracaną.  
  
2. Aby uprościć dostęp do `MarshalAs` atrybutu, `Imports` Dodaj instrukcję do górnej części kodu dla klasy lub modułu, jak w poniższym przykładzie:  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
3. Dodaj prototyp funkcji dla zaimportowanej funkcji do używanej klasy lub modułu i Zastosuj `MarshalAs` atrybut do parametrów lub wartości zwracanej. W poniższym przykładzie wywołanie interfejsu API, które oczekuje typu `void*` , jest organizowane jako: `AsAny`  
  
     [!code-vb[VbVbalrInterop#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#14)]  
  
## <a name="api-calls-using-dllimport"></a>Wywołania interfejsu API używające DllImport  
 Ten `DllImport` atrybut stanowi drugi sposób wywoływania funkcji w bibliotekach DLL bez bibliotek typów. `DllImport`jest w przybliżeniu równy użyciu instrukcji `Declare` , ale zapewnia większą kontrolę nad sposobem wywołania funkcji.  
  
 Można używać `DllImport` z większością wywołań interfejsu API systemu Windows, o ile wywołanie odwołuje się do udostępnionej metody (nazywanej czasem *statyczną*). Nie można użyć metod, które wymagają wystąpienia klasy. W przeciwieństwie `Declare` do `DllImport` instrukcji, wywołania nie `MarshalAs` mogą używać atrybutu.  
  
### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>Aby wywołać interfejs API systemu Windows przy użyciu atrybutu DllImport  
  
1. Otwórz nowy projekt aplikacji systemu Windows, klikając pozycję **Nowy** w menu **plik** , a następnie klikając pozycję **projekt**. **Nowy projekt** pojawi się okno dialogowe.  
  
2. Wybierz pozycję **aplikacja systemu Windows** z listy Visual Basic szablonów projektu. Zostanie wyświetlony nowy projekt.  
  
3. Dodaj przycisk o nazwie `Button2` do formularza startowego.  
  
4. Kliknij `Button2` dwukrotnie, aby otworzyć widok kodu dla formularza.  
  
5. Aby uprościć dostęp `DllImport`do programu, `Imports` Dodaj instrukcję na początku kodu dla klasy formularza startowego:  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
6. Zadeklaruj pustą funkcję poprzedzającą `End Class` instrukcję dla formularza i nazwij funkcję. `MoveFile`  
  
7. Zastosuj Modyfikatory `Shared` `MoveFile` i do deklaracji funkcji i ustaw parametry na podstawie argumentów używanych przez funkcję interfejsu API systemu Windows: `Public`  
  
     [!code-vb[VbVbalrInterop#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#16)]  
  
     Funkcja może mieć dowolną poprawną nazwę procedury; Ten `DllImport` atrybut określa nazwę w bibliotece DLL. Obsługuje ona również kierowanie współdziałania dla parametrów i wartości zwracanych, dzięki czemu można wybrać typy danych programu Visual Studio, które są podobne do typów danych używanych przez interfejs API.  
  
8. `DllImport` Zastosuj atrybut do pustej funkcji. Pierwszy parametr jest nazwą i lokalizacją biblioteki DLL zawierającej wywoływaną funkcję. Nie trzeba określać ścieżki dla plików znajdujących się w katalogach systemu Windows. Drugi parametr jest argumentem nazwanym, który określa nazwę funkcji w interfejsie API systemu Windows. W tym przykładzie `DllImport` atrybut wymusza przekazywanie `MoveFile` wywołań `MoveFileW` do w programie Kernel32. Bibliotece. Metoda kopiuje plik ze ścieżki `src` do ścieżki `dst`. `MoveFileW`  
  
     [!code-vb[VbVbalrInterop#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#17)]  
  
9. Dodaj kod do `Button2_Click` programu obsługi zdarzeń, aby wywołać funkcję:  
  
     [!code-vb[VbVbalrInterop#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#18)]  
  
10. Utwórz plik o nazwie test. txt i umieść go w katalogu C:\Tmp na dysku twardym. W razie potrzeby Utwórz katalog tmp.  
  
11. Naciśnij klawisz F5, aby uruchomić aplikację. Zostanie wyświetlony formularz główny.  
  
12. Kliknij pozycję **Button2**. Komunikat "pomyślnie przeniesiono plik" jest wyświetlany, jeśli plik może zostać przeniesiony.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)
- [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Tworzenie prototypów w kodzie zarządzanym](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [Marshaling delegata jako metoda wywołania zwrotnego](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
