---
title: "Wskazówki: wywoływanie Windows API (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d494ad0f8bd4eb0dac57de214064fd2d208011ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>Wskazówki: wywoływanie Windows API (Visual Basic)
Interfejsy API systemu Windows są bibliotek dołączanych (dynamicznie dll), które są częścią systemu operacyjnego Windows. Użyj ich do wykonywania zadań, gdy jest trudne do zapisania równoważnych procedur własny. Na przykład system Windows udostępnia funkcję o nazwie `FlashWindowEx` która pozwala na pasku tytułu aplikacji alternatywny między jasnym i ciemnym.  
  
 Zaletą używania interfejsów API systemu Windows w kodzie jest, aby móc zapisać czasie opracowywania ponieważ zawierają one dziesiątki przydatne funkcje, które są już zapisane i poczekać do użycia. Wadą jest to, że interfejsów API systemu Windows może być trudne do pracy z i unforgiving, w przypadku wystąpienia problemów.  
  
 Interfejsy API systemu Windows reprezentują kategorii specjalnej współdziałania. Interfejsy API systemu Windows nie korzystają z kodu zarządzanego, nie mają wbudowanej biblioteki typów, a następnie użyj typów danych, które są inne niż te używane z programem Visual Studio. Z powodu różnic a ponieważ interfejsów API systemu Windows nie są obiekty COM, współdziałanie z interfejsów API systemu Windows i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] odbywa się przy użyciu platformy invoke, lub funkcji PInvoke. Wywołanie platformy to usługa, że umożliwia zarządzanego kodu wywoływanie niezarządzanych funkcji zaimplementowana w bibliotekach DLL. Aby uzyskać więcej informacji, zobacz [wykorzystywanie niezarządzanych funkcji DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md). Można użyć funkcji PInvoke w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] za pomocą `Declare` instrukcji lub stosowania `DllImport` atrybutu pustej procedury.  
  
 Wywołania interfejsu API systemu Windows zostały ważnym elementem [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Programowanie w przeszłości, ale są rzadko niezbędne wraz z programem Visual Basic .NET. Jeśli to możliwe, należy użyć kodu zarządzanego z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] do wykonywania zadań, zamiast wywołania interfejsu API systemu Windows. Ten przewodnik zawiera informacje dotyczące tych sytuacji, w których przy użyciu interfejsów API systemu Windows jest to konieczne.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>Deklarowanie przy użyciu interfejsu API  
 Typowym sposobem wywoływanie Windows API jest za pomocą `Declare` instrukcji.  
  
#### <a name="to-declare-a-dll-procedure"></a>Aby zadeklarować procedury biblioteki DLL  
  
1.  Określić nazwę funkcji, do której ma zostać wywołana, oraz jego argumenty, typy argumentów i zwraca wartość, a także nazwę i lokalizację biblioteki dll, która go zawiera.  
  
    > [!NOTE]
    >  Aby uzyskać pełne informacje na temat interfejsów API systemu Windows zobacz dokumentację Win32 SDK w interfejsie Windows API zestawu SDK platformy. Aby uzyskać więcej informacji na temat stałe, które używają interfejsów API systemu Windows Sprawdź pliki nagłówkowe, takich jak Windows.h dołączone do zestawu SDK platformy.  
  
2.  Otwórz nowy projekt aplikacji systemu Windows, klikając przycisk **nowy** na **pliku** menu, a następnie klikając pozycję **projektu**. **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
3.  Wybierz **aplikacji systemu Windows** z listy [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] szablony projektu. Zostanie wyświetlony nowy projekt.  
  
4.  Dodaj następujące `Declare` działać na klasę lub moduł, w której chcesz użyć biblioteki DLL:  
  
     [!code-vb[VbVbalrInterop#9](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]  
  
### <a name="parts-of-the-declare-statement"></a>Części Declare — instrukcja  
 `Declare` Instrukcji obejmuje następujące elementy.  
  
#### <a name="auto-modifier"></a>Modyfikator Auto  
 `Auto` Modyfikator powoduje, że środowisko uruchomieniowe można przekonwertować ciągu na podstawie nazwy metody zgodnie z reguł środowiska uruchomieniowego języka wspólnego (lub nazwę aliasu, jeśli zostanie określona).  
  
#### <a name="lib-and-alias-keywords"></a>Słowa kluczowe lib i Alias  
 Następujące nazwy `Function` — słowo kluczowe to nazwa programu używa do uzyskiwania dostępu importowanych funkcji. Może być taka sama jak rzeczywista nazwa wywoływania funkcji lub można użyć procedury prawidłową nazwę, a następnie u `Alias` — słowo kluczowe, aby określić nazwę rzeczywistych wywoływania funkcji.  
  
 Określ `Lib` — słowo kluczowe, a po nim nazwę i lokalizację biblioteki dll, która zawiera funkcję wywoływania. Nie trzeba określić ścieżkę do plików znajdujących się w katalogach systemu Windows.  
  
 Użyj `Alias` — słowo kluczowe, jeśli nie jest prawidłową nazwą funkcji wywoływania [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nazwę procedury lub powoduje konflikt z nazwą innych elementów w aplikacji. `Alias`Wskazuje wartość true, nazwę wywoływanej funkcji.  
  
#### <a name="argument-and-data-type-declarations"></a>Argument i deklaracje typu danych  
 Deklaruje argumentów i ich typów danych. Ta część może być wyzwaniem, ponieważ typy danych, które korzysta z systemu Windows nie są zgodne typy danych Visual Studio. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]jak dużo pracy, w przypadku można konwertując argumenty kompatybilne typy danych, w procesie nazywanym *marshaling*. Można jawnie kontrolować sposób argumenty są przekazywane za pomocą <xref:System.Runtime.InteropServices.MarshalAsAttribute> zdefiniowanych w atrybucie <xref:System.Runtime.InteropServices> przestrzeni nazw.  
  
> [!NOTE]
>  Poprzednie wersje [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] umożliwiająca deklarować parametrów `As Any`, co oznacza danych wszelkich danych typu można użyć. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]wymaga, aby używać typu danych określonego dla wszystkich `Declare` instrukcje.  
  
#### <a name="windows-api-constants"></a>Stałe Windows API  
 Niektóre argumenty są kombinację stałych. Na przykład `MessageBox` interfejsu API wyświetlane w tym przewodniku akceptuje argument liczby całkowitej o nazwie `Typ` steruje sposób wyświetlania pola wiadomości. Można określić wartość liczbowa te stałe, sprawdzając `#define` instrukcje w pliku WinUser.h. Wartości numeryczne zazwyczaj są wyświetlane w formacie szesnastkowym, więc możesz je dodać, a następnie wykonać konwersję dziesiętnych przy użyciu kalkulatora. Na przykład, jeśli chcesz połączyć stałe stylu wykrzyknika `MB_ICONEXCLAMATION` 0x00000030 i tak/nie styl `MB_YESNO` 0x00000004, możesz dodać liczb i uzyskanie wyniku 0x00000034 lub 52 dziesiętną. Chociaż można używać bezpośrednio wynik decimal, zaleca się Zadeklaruj te wartości jako stałe w aplikacji, a następnie ich łączenie za pomocą `Or` operatora.  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a>Deklarowanie stałych dla wywołania interfejsu API systemu Windows  
  
1.  Dokumentacja funkcji systemu Windows, z którym nawiązywane jest. Określ nazwę stałe, które są używane i nazwę pliku .h, zawierająca wartości liczbowe dla tych stałych.  
  
2.  Użyj edytora tekstów, takiego jak Notatnik, aby wyświetlić zawartość pliku nagłówków (.h) i Znajdź wartości skojarzone z stałe, którego używasz. Na przykład `MessageBox` stała używa interfejsu API `MB_ICONQUESTION` pokazanie znak zapytania w oknie komunikatu. Definicja `MB_ICONQUESTION` jest WinUser.h i wygląda następująco:  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  Dodaj równoważne `Const` instrukcje do klasy lub moduł, aby udostępnić te stałe do aplikacji. Na przykład:  
  
     [!code-vb[VbVbalrInterop#11](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]  
  
###### <a name="to-call-the-dll-procedure"></a>Aby wywołać procedurę biblioteki DLL  
  
1.  Dodawanie przycisku o nazwie `Button1` do uruchamiania formularza do projektu, a następnie kliknij dwukrotnie, aby wyświetlić jego kod. Program obsługi zdarzeń dla przycisku jest wyświetlany.  
  
2.  Dodaj kod, aby `Click` programu obsługi zdarzeń dla przycisku, należy dodać do wywołania tej procedury i podaj odpowiednie argumenty:  
  
     [!code-vb[VbVbalrInterop#12](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]  
  
3.  Uruchom projekt, naciskając klawisz F5. Komunikat jest wyświetlany zarówno **tak** i **nr** przyciski odpowiedzi. Kliknij dowolny.  
  
#### <a name="data-marshaling"></a>Przekazywanie danych  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]automatycznie konwertuje typów danych parametrów i wartości zwracane dla wywołania interfejsu API systemu Windows, ale można użyć `MarshalAs` atrybutu, aby jawnie określić typy niezarządzanych danych, które oczekuje interfejsu API. Aby uzyskać więcej informacji na temat marshaling międzyoperacyjny zobacz [organizowanie międzyoperacyjne](../../../framework/interop/interop-marshaling.md).  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>Aby użyć Declare i MarshalAs w wywołaniu interfejsu API  
  
1.  Określić nazwę funkcji chcesz się połączyć, oraz jej argumenty typów danych i zwracają wartość.  
  
2.  Aby uprościć dostęp do `MarshalAs` atrybutu, Dodaj `Imports` instrukcji na początku kod klasę lub moduł, jak w poniższym przykładzie:  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
3.  Dodaj prototyp funkcji dla funkcji zaimportowane do klasę lub moduł, a zastosowanie `MarshalAs` atrybutów do parametrów wyjściowych ani zwracanej wartości. W poniższym przykładzie, wywołanie interfejsu API, która oczekuje typu `void*` jest przekazywane jako `AsAny`:  
  
     [!code-vb[VbVbalrInterop#14](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]  
  
## <a name="api-calls-using-dllimport"></a>Wywołania API przy użyciu atrybutu DllImport  
 `DllImport` Atrybutu zawiera drugi sposób wywołania funkcji w bibliotekach DLL bez biblioteki typów. `DllImport`jest w przybliżeniu przy użyciu `Declare` instrukcji, ale zapewnia większą kontrolę nad jak noszą nazwę funkcji.  
  
 Można użyć `DllImport` z większości interfejsu API systemu Windows wywołuje tak długo, jak wywołanie odwołuje się do udostępnionej (nazywane również *statycznych*) — metoda. Nie można użyć metody, które wymagają wystąpienia klasy. W odróżnieniu od `Declare` instrukcji `DllImport` nie mogą używać wywołania `MarshalAs` atrybutu.  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>Aby wywołać interfejs API systemu Windows przy użyciu atrybutu DllImport  
  
1.  Otwórz nowy projekt aplikacji systemu Windows, klikając przycisk **nowy** na **pliku** menu, a następnie klikając pozycję **projektu**. **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
2.  Wybierz **aplikacji systemu Windows** z listy [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] szablony projektu. Zostanie wyświetlony nowy projekt.  
  
3.  Dodawanie przycisku o nazwie `Button2` się formularz startowy.  
  
4.  Kliknij dwukrotnie `Button2` do otwierania widoku kodu formularza.  
  
5.  Aby uprościć dostęp do `DllImport`, Dodaj `Imports` instrukcji na początku kod klasy formularz startowy:  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
6.  Deklaruje funkcję pusty poprzedniego `End Class` instrukcji formularza i nazwa funkcji `MoveFile`.  
  
7.  Zastosuj `Public` i `Shared` Modyfikatory deklaracji funkcji i ustawianie parametrów `MoveFile` oparto na argumentach funkcji interfejsu API systemu Windows:  
  
     [!code-vb[VbVbalrInterop#16](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]  
  
     Funkcja może mieć dowolną nazwę procedury prawidłowe; `DllImport` atrybut określa nazwę w bibliotece DLL. Umożliwia on również obsługę współdziałanie przekazywanie parametrów i zwracanych wartości, więc możesz wybrać typy danych Visual Studio, które są podobne do danych typów używa interfejsu API.  
  
8.  Zastosuj `DllImport` do funkcji pusty atrybut. Pierwszym parametrem jest nazwy i lokalizacji pliku DLL zawierającego wywoływana funkcja. Nie trzeba określić ścieżkę do plików znajdujących się w katalogach systemu Windows. Drugi parametr jest nazwany argument, który określa nazwę funkcji interfejsu API systemu Windows. W tym przykładzie `DllImport` atrybutu wymusza wywołań `MoveFile` do przekazania do `MoveFileW` w KERNEL32. BIBLIOTEKI DLL. `MoveFileW` Metody kopiuje plik ze ścieżki `src` na ścieżkę `dst`.  
  
     [!code-vb[VbVbalrInterop#17](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]  
  
9. Dodaj kod, aby `Button2_Click` obsługi zdarzeń w wywołaniu funkcji:  
  
     [!code-vb[VbVbalrInterop#18](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]  
  
10. Utwórz plik o nazwie Test.txt i umieszczenie go w katalogu C:\Tmp na dysku twardym. Utwórz katalog Tmp, jeśli to konieczne.  
  
11. Naciśnij klawisz F5, aby uruchomić aplikację. Zostanie wyświetlony formularz główny.  
  
12. Kliknij przycisk **Button2**. Komunikat "plik przeniesiono pomyślnie" jest wyświetlana, jeśli można przenieść pliku.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [DECLARE — instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Automatycznie](../../../visual-basic/language-reference/modifiers/auto.md)  
 [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)  
 [Współdziałanie z COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tworzenie prototypów w kodzie zarządzanym](../../../framework/interop/creating-prototypes-in-managed-code.md)  
 [Marshaling delegata jako metoda wywołania zwrotnego](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
