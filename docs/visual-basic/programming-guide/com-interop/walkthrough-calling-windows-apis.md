---
title: 'Przewodnik: Wywoływanie Windows API (Visual Basic)'
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
ms.openlocfilehash: 8fd63c2abedcd416937e2c281486bdc1716a275f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022405"
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>Przewodnik: Wywoływanie Windows API (Visual Basic)
Interfejsy API Windows są bibliotek dołączanych dynamicznie (dll), które są częścią systemu operacyjnego Windows. Użyj ich do wykonywania zadań, gdy jest trudne do pisania procedur równoważne własne. Na przykład Windows zapewnia funkcję o nazwie `FlashWindowEx` gwarantowaną na pasku tytułu aplikacji alternatywne między poszczególnymi jasny i ciemny.  
  
 Zaletą korzystania z Windows API w kodzie jest, aby mogli oszczędzać czas projektowania, ponieważ zawierają one wielu przydatnych funkcji, które zostały już napisane i długiego czasu oczekiwania ma być używany. Wadą jest to, że interfejsy API Windows może być trudne do pracy z i unforgiving, gdy coś pójdzie źle.  
  
 Interfejsy API Windows reprezentują kategorii specjalnej współdziałania. Interfejsy API Windows korzysta z kodu zarządzanego, nie mają wbudowanej wpisz biblioteki i używać typów danych, które są inne niż te używane w programie Visual Studio. Ze względu na następujące różnice a ponieważ interfejsy API Windows nie są obiektami COM, współpracy z interfejsami API Windows i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] odbywa się przy użyciu platformy wywołać, lub jako PInvoke. Wywołanie platformy jest usługą, które umożliwia zarządzanemu kodowi do wywołania funkcji niezarządzanych zaimplementowane w bibliotekach DLL. Aby uzyskać więcej informacji, zobacz [wykorzystywanie niezarządzanych funkcji DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md). Możesz używać PInvoke w języku Visual Basic, przy użyciu `Declare` instrukcji lub stosowanie `DllImport` atrybut pusty procedury.  
  
 Wywołania interfejsu API Windows ważnym elementem programowania w przeszłości Visual Basic zostały, ale rzadko są niezbędne przy użyciu programu Visual Basic .NET. W miarę możliwości, skorzystaj z kodu zarządzanego z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] do wykonywania zadań, a nie wywołań interfejsu API Windows. Ten przewodnik zawiera informacje dotyczące tych sytuacji, w której przy użyciu interfejsów API Windows jest to konieczne.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>Zadeklaruj przy użyciu interfejsu API  
 Najczęstszym sposobem wywoływania interfejsów API Windows polega na użyciu `Declare` instrukcji.  
  
#### <a name="to-declare-a-dll-procedure"></a>Aby zadeklarować procedury biblioteki DLL  
  
1. Określić nazwę funkcji, której chcesz się połączyć, oraz jego argumentów, typy argumentów i zwracać wartości, a także nazwę i lokalizację biblioteki DLL, która go zawiera.  
  
    > [!NOTE]
    >  Aby uzyskać pełne informacje o interfejsach API Windows zobacz dokumentację zestawu SDK systemu Win32 w interfejsie API Windows SDK platformy. Aby uzyskać więcej informacji na temat stałe, które używają interfejsów API Windows Sprawdź pliki nagłówkowe, takie jak Windows.h dołączone do zestawu SDK platformy.  
  
2. Otwórz nowy projekt aplikacji Windows, klikając **New** na **pliku** menu, a następnie klikając polecenie **projektu**. **Nowy projekt** pojawi się okno dialogowe.  
  
3. Wybierz **aplikacji Windows** z listy szablonów projektu języka Visual Basic. Zostanie wyświetlony nowy projekt.  
  
4. Dodaj następujący kod `Declare` funkcję na klasę lub moduł, w której chcesz użyć biblioteki DLL:  
  
     [!code-vb[VbVbalrInterop#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#9)]  
  
### <a name="parts-of-the-declare-statement"></a>Części Declare — instrukcja  
 `Declare` Wyciąg zawiera następujące elementy.  
  
#### <a name="auto-modifier"></a>Modyfikator Auto  
 `Auto` Modyfikator powoduje, że środowisko uruchomieniowe do konwersji ciągu na podstawie nazwy metody, zgodnie z typowych reguł środowiska uruchomieniowego języka (lub nazwę aliasu, jeśli określono).  
  
#### <a name="lib-and-alias-keywords"></a>Słowa kluczowe lib i Alias.  
 Następujące nazwy `Function` — słowo kluczowe nazywa się program używa do importowanych funkcji dostępu. Może być taka sama jak rzeczywistą nazwą funkcji, którą wywołujesz, albo można użyć dowolnej nazwy prawidłowe procedury i następnie stosują `Alias` — słowo kluczowe, aby określić rzeczywistą nazwą funkcji, którą wywołujesz.  
  
 Określ `Lib` — słowo kluczowe, a następnie nazwę i lokalizację biblioteki DLL, która zawiera funkcję, którą wywołujesz. Nie ma potrzeby określ ścieżkę do plików znajdujących się w katalogach systemu Windows.  
  
 Użyj `Alias` — słowo kluczowe, jeśli nazwa funkcji wywołanie nie jest prawidłową nazwą procedury języka Visual Basic lub powoduje konflikt z nazwą innych elementów w aplikacji. `Alias` Wskazuje wartość true, nazwę wywoływanej funkcji.  
  
#### <a name="argument-and-data-type-declarations"></a>Argument i deklaracji typów danych  
 Zadeklaruj argumentów i ich typy danych. Ta część może stanowić wyzwanie, ponieważ typy danych, które używa Windows nie są zgodne typy danych Visual Studio. Visual Basic jest dużo pracy dla Ciebie konwertując argumenty kompatybilne typy danych, w procesie zwanym *marshaling*. Można jawnie kontrolować, jak argumenty są przekazywane przy użyciu <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutowi określonemu w <xref:System.Runtime.InteropServices> przestrzeni nazw.  
  
> [!NOTE]
>  Poprzednie wersje języka Visual Basic można deklarować parametrów `As Any`, co oznacza danych wszelkich danych typu można użyć. Visual Basic wymaga użycia określonego typu danych dla wszystkich `Declare` instrukcji.  
  
#### <a name="windows-api-constants"></a>Stałe Windows API  
 Niektóre argumenty są kombinacje stałe. Na przykład `MessageBox` przedstawione w niniejszym instruktażu interfejs API akceptuje argument liczby całkowitej o nazwie `Typ` sterującą, jak zostanie wyświetlone okno komunikatu. Można określić wartość liczbową te stałe, sprawdzając `#define` instrukcje w pliku WinUser.h. Wartości numeryczne są wyświetlane w formacie szesnastkowym, ogólnie, więc możesz je dodać i Konwertuj na wartość dziesiętną przy użyciu kalkulatora. Na przykład, jeśli chcesz połączyć stałe dla stylu wykrzyknika `MB_ICONEXCLAMATION` 0x00000030 i tak/bez stylu `MB_YESNO` 0x00000004, można dodać liczb i uzyskanie wyniku 0x00000034 lub 52 dziesiętną. Chociaż można używać wyniku dziesiętna bezpośrednio, zaleca się deklarować te wartości jako stałe w aplikacji, a także połączyć je przy użyciu `Or` operatora.  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a>Aby zadeklarować stałe dla wywołań interfejsu API Windows  
  
1. Zajrzyj do dokumentacji dla funkcji Windows, którą wywołujesz. Określ nazwę stałe, które są używane i nazwę pliku .h, zawierająca wartości liczbowe dla tych stałych.  
  
2. Użyj edytora tekstu, takiego jak Notatnik, aby wyświetlić zawartość pliku nagłówka (.h) i Znajdź wartości skojarzone z stałe, którego używasz. Na przykład `MessageBox` interfejsu API używa stałej `MB_ICONQUESTION` do wyświetlenia znaku zapytania w oknie komunikatu. Definicja `MB_ICONQUESTION` jest WinUser.h i wygląda następująco:  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3. Dodaj odpowiednik `Const` instrukcji do klasy lub modułu, aby udostępnić te stałe do aplikacji. Na przykład:  
  
     [!code-vb[VbVbalrInterop#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#11)]  
  
###### <a name="to-call-the-dll-procedure"></a>Aby wywołać procedurę biblioteki DLL  
  
1. Dodaj przycisk o nazwie `Button1` do uruchamiania formularza do projektu, a następnie go dwukrotnie, aby wyświetlić jej kod. Program obsługi zdarzeń dla przycisku zostanie wyświetlona.  
  
2. Dodaj kod, aby `Click` programu obsługi zdarzeń dla przycisku został dodany, aby wywołać procedurę i podaj odpowiednie argumenty:  
  
     [!code-vb[VbVbalrInterop#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#12)]  
  
3. Uruchom projekt, naciskając klawisz F5. Zostanie wyświetlone okno komunikatu, zarówno **tak** i **nie** przyciski odpowiedzi. Kliknij jeden.  
  
#### <a name="data-marshaling"></a>Marshaling danych  
 Visual Basic automatycznie konwertuje typów danych parametrów i wartości zwracane dla wywołań interfejsu API Windows, ale można użyć `MarshalAs` atrybutu, aby jawnie określić typy niezarządzanych danych, których oczekuje interfejs API. Aby uzyskać więcej informacji na temat marshaling międzyoperacyjny zobacz [Marshaling międzyoperacyjności](../../../framework/interop/interop-marshaling.md).  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>Aby użyć Declare i MarshalAs w wywołaniu interfejsu API  
  
1. Określ nazwę funkcji, którą chcesz wywołać oraz jej argumenty typów danych i zwracają wartość.  
  
2. Aby uprościć dostęp do `MarshalAs` atrybutu, należy dodać `Imports` instrukcji na górze kod klasę lub moduł, tak jak w poniższym przykładzie:  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
3. Dodaj prototypu funkcji dla importowanych funkcji w klasie lub modułu, a zastosowanie `MarshalAs` atrybutu do parametrów lub wartości zwracanej. W poniższym przykładzie wywołanie interfejsu API, która oczekuje typu `void*` jest organizowana jako `AsAny`:  
  
     [!code-vb[VbVbalrInterop#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#14)]  
  
## <a name="api-calls-using-dllimport"></a>Wywołania interfejsu API przy użyciu elementu DllImport  
 `DllImport` Atrybut zawiera druga metoda do wywołania funkcji w bibliotekach DLL bez biblioteki typów. `DllImport` jest w przybliżeniu za pomocą `Declare` instrukcji, ale zapewnia większą kontrolę nad jak funkcje są wywoływane.  
  
 Możesz użyć `DllImport` z większości API Windows wywołuje tak długo, jak wywołanie odnosi się do udostępnionego (nazywane czasem *statyczne*) metody. Nie można używać metod, które wymagają wystąpienia klasy. W odróżnieniu od `Declare` instrukcji `DllImport` nie mogą używać wywołania `MarshalAs` atrybutu.  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>Aby wywołać interfejs API Windows za pomocą atrybutu DllImport  
  
1. Otwórz nowy projekt aplikacji Windows, klikając **New** na **pliku** menu, a następnie klikając polecenie **projektu**. **Nowy projekt** pojawi się okno dialogowe.  
  
2. Wybierz **aplikacji Windows** z listy szablonów projektu języka Visual Basic. Zostanie wyświetlony nowy projekt.  
  
3. Dodaj przycisk o nazwie `Button2` do formy uruchamiania.  
  
4. Kliknij dwukrotnie `Button2` otwarcie widoku kodu formularza.  
  
5. Aby uprościć dostęp do `DllImport`, Dodaj `Imports` instrukcji na górze kod startowy klasy formularza:  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
6. Deklarowanie funkcji empty poprzedniego `End Class` instrukcji formularza i nazwy funkcji `MoveFile`.  
  
7. Zastosuj `Public` i `Shared` Modyfikatory do deklaracji funkcji i ustawianie parametrów `MoveFile` na podstawie argumentów korzysta z funkcji Windows API:  
  
     [!code-vb[VbVbalrInterop#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#16)]  
  
     Funkcja może mieć dowolną nazwę procedury prawidłowe; `DllImport` atrybut określa nazwę w bibliotece DLL. Umożliwia on również obsługę współdziałanie marshaling dla parametrów i wartości zwracane, więc możesz wybrać typy danych Visual Studio, które są podobne do danych typy używa interfejsu API.  
  
8. Zastosuj `DllImport` atrybutu do funkcji empty. Pierwszy parametr jest nazwę i lokalizację pliku DLL zawierającego funkcję, którą wywołujesz. Nie ma potrzeby określ ścieżkę do plików znajdujących się w katalogach systemu Windows. Drugi parametr jest nazwany argument, który określa nazwę funkcji w interfejsie API Windows. W tym przykładzie `DllImport` atrybut wymusza wywołania `MoveFile` były przekazywane do `MoveFileW` w KERNEL32. BIBLIOTEKI DLL. `MoveFileW` Metoda służy do kopiowania pliku ze ścieżki `src` do ścieżki `dst`.  
  
     [!code-vb[VbVbalrInterop#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#17)]  
  
9. Dodaj kod, aby `Button2_Click` program obsługi zdarzeń w wywołaniu funkcji:  
  
     [!code-vb[VbVbalrInterop#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#18)]  
  
10. Utwórz plik o nazwie jako i umieść go w katalogu C:\Tmp na dysku twardym. Utwórz katalog Tmp, jeśli to konieczne.  
  
11. Naciśnij klawisz F5, aby uruchomić aplikację. Zostanie wyświetlony formularz główny.  
  
12. Kliknij przycisk **Button2**. Jeśli można przenieść pliku, jest wyświetlany komunikat "plik przeniesiono pomyślnie".  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)
- [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Tworzenie prototypów w kodzie zarządzanym](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [Marshaling delegata jako metoda wywołania zwrotnego](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
