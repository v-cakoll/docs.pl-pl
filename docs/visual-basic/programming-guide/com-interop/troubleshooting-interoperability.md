---
title: Rozwiązywanie problemów związanych z współdziałaniem (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop, deploying assemblies
- assemblies [Visual Basic]
- interop, installing assemblies that share components
- COM objects, troubleshooting
- interop, sharing components
- troubleshooting interoperability [Visual Basic]
- interoperability, troubleshooting
- COM interop [Visual Basic], troubleshooting
- assemblies [Visual Basic], deploying
- troubleshooting Visual Basic, interoperability
- interop assemblies
- interoperability, sharing components
- shared components, using with assemblies
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
ms.openlocfilehash: 65005dbbe42f52b3159c8e595972dace3064f986
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643708"
---
# <a name="troubleshooting-interoperability-visual-basic"></a>Rozwiązywanie problemów związanych z współdziałaniem (Visual Basic)
Gdy współpraca między COM i kod zarządzany [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], mogą wystąpić co najmniej jeden z następujących typowych problemów.  
  
##  <a name="vbconinteroperabilitymarshalinganchor1"></a> Przekazywanie międzyoperacyjne  
 W czasie, należy użyć typów danych, które nie są częścią [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Zestawy międzyoperacyjne obsługiwać większość pracy dla obiektów COM, ale może być konieczne kontrolować typów danych, które są używane, gdy obiekty zarządzane są widoczne dla modelu COM. Na przykład określić struktury w bibliotekach klas `BStr` niezarządzany typ na ciągach wysyłane do obiektów COM utworzonych przez Visual Basic 6.0 i starszych wersji. W takich przypadkach można użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu spowodować typy zarządzane mają być uwidaczniane jako typy niezarządzane.  
  
##  <a name="vbconinteroperabilitymarshalinganchor2"></a> Eksportowanie do kodu niezarządzanego ciągi o stałej długości  
 W Visual Basic 6.0 i starszych wersjach ciągi zostaną wyeksportowane do obiektów COM jako sekwencję bajtów bez znaku zakończenia o wartości null. Zgodność z innymi językami Visual Basic .NET zawiera znak zakończenia podczas eksportowania ciągów. Najlepszym sposobem rozwiązania tej niezgodności nie jest eksportowane ciągów, których brakuje znaku zakończenia jako tablice `Byte` lub `Char`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor3"></a> Eksportowanie hierarchii dziedziczenia  
 Zarządzane klasy hierarchie spłaszczanie wychodzących, gdy udostępniony jako obiekty COM. Na przykład jeśli definiuje klasę podstawową z elementem członkowskim, a następnie dziedziczyć klasa podstawowa w klasie pochodnej uwidocznioną jak dla obiektu COM, klientów, którzy używają klasy pochodnej w obiekcie COM nie będzie mógł używać dziedziczone elementy członkowskie. Elementów członkowskich klasy podstawowej są dostępne z obiektów COM tylko wystąpienia klasy podstawowej, a następnie tylko wtedy, gdy tworzona jest również klasy podstawowej jako obiekt COM.  
  
## <a name="overloaded-methods"></a>Metody przeciążane  
 Chociaż przeciążonych metod można tworzyć za pomocą Visual Basic, nie są obsługiwane przez COM. Gdy klasa, która zawiera przeciążonej metody jest ujawniona jako obiekt COM, nowe nazwy metody są generowane dla przeciążonej metody.  
  
 Rozważmy na przykład klasy, która ma dwa przeciążenia `Synch` metody. Jeśli klasa jest ujawniona jako obiekt COM, nowych nazw wygenerowane metody może być `Synch` i `Synch_2`.  
  
 Zmiana nazwy może spowodować problemy w dwóch dla konsumentów obiektu COM.  
  
1.  Klienci nie mogą wymagać nazwy metod wygenerowany.  
  
2.  Po dodaniu nowego przeciążeń klasy lub jej klasa podstawowa, można zmienić nazwy wygenerowane metody w klasie udostępniony jako obiekt COM. Może to powodować problemy przechowywania wersji.  
  
 Aby rozwiązać problemy z obu, nadaj każdej metodzie unikatową nazwę, zamiast przeładowanie podczas opracowywania obiektów, które mają być widoczne jako obiekty COM.  
  
##  <a name="vbconinteroperabilitymarshalinganchor4"></a> Korzystanie z obiektów COM za pomocą zestawy międzyoperacyjne  
 Możesz użyć zestawy międzyoperacyjne niemal tak, jakby były kodu zarządzanego zastępujące obiektów COM, które reprezentują. Jednak ponieważ są one otoki, a nie rzeczywiste obiektów COM, istnieją pewne różnice między używaniem zestawy międzyoperacyjne i standardowe zestawy. Te obszary różnicy to narażenia klas i typów danych parametrów i zwracanych wartości.  
  
##  <a name="vbconinteroperabilitymarshalinganchor5"></a> Klasy widoczne jako dotyczą obu interfejsów i klasy  
 W przeciwieństwie do klas w standardowe zestawy klasy COM są widoczne w zestawy międzyoperacyjne jako klasa, która reprezentuje klasy COM i interfejsu. Nazwa interfejsu jest identyczna jak klasa COM. Nazwa klasy międzyoperacyjny jest takie samo jak oryginalne klasy COM, ale ze słowem "Class" jest dołączany. Załóżmy na przykład projektu z odwołania do zestawu międzyoperacyjnego dla obiekt COM. Jeśli nosi nazwę klasy COM `MyComClass`, IntelliSense i przeglądarka obiektów Pokaż interfejs o nazwie `MyComClass` i klasę o nazwie `MyComClassClass`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor6"></a> Tworzenie wystąpienia klasy .NET Framework  
 Ogólnie rzecz biorąc, można utworzyć wystąpienia [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] przy użyciu `New` instrukcję, określając nazwę klasy. Klasy COM reprezentowany przez zestaw międzyoperacyjny jest jeden przypadek, w którym można użyć `New` instrukcji przy użyciu interfejsu. Tylko w przypadku korzystania z klasy COM `Inherits` instrukcji, można użyć interfejsu, tak jak w klasie. Poniższy kod przedstawia sposób tworzenia `Command` obiektu w projekcie, który zawiera odwołanie do obiektu Microsoft ActiveX danych obiektów 2.8 biblioteki COM:  
  
 [!code-vb[VbVbalrInterop#20](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_1.vb)]  
  
 Jeśli używasz klasy COM jako podstawa dla klasy pochodnej, musi jednak użyć międzyoperacyjnego klasa, która reprezentuje klasy COM, zgodnie z poniższym kodem:  
  
 [!code-vb[VbVbalrInterop#21](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_2.vb)]  
  
> [!NOTE]
>  Zestawy międzyoperacyjne niejawnie zaimplementować interfejsów, które reprezentują klasy COM. Nie należy próbować użyć `Implements` spowoduje instrukcji do realizacji tych interfejsów lub wystąpił błąd.  
  
##  <a name="vbconinteroperabilitymarshalinganchor7"></a> Typy danych dla parametrów i zwracanych wartości  
 W przeciwieństwie do członków standardowe zestawy zestawu międzyoperacyjnego członkowie mogą mieć typów danych, które różnią się od używanych w oryginalnej deklaracji obiektu. Mimo że zestawy międzyoperacyjne niejawnie przekonwertować typów COM niezgodne typy środowiska uruchomieniowego języka wspólnego, należy zwrócić uwagę na typy danych, które są używane przez obie strony, aby zapobiec wystąpieniu błędów czasu wykonywania. Na przykład w modelu COM obiektów tworzonych w Visual Basic 6.0 i starszych wersjach, wartości typu `Integer` założono [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] odpowiednik typu `Short`. Zalecane jest, użyj przeglądarki obiektów do sprawdzenia właściwości elementów członkowskich zaimportowane przed ich użyciem.  
  
##  <a name="vbconinteroperabilitymarshalinganchor8"></a> Moduł metody na poziomie modelu COM  
 Większość obiektów COM są używane przez utworzenie wystąpienia klasy modelu COM przy użyciu `New` — słowo kluczowe, a następnie podczas wywoływania metody obiektu. Jedynym wyjątkiem od tej reguły obejmuje obiekty COM, które zawierają `AppObj` lub `GlobalMultiUse` klasy COM. Takie klasy przypominać modułu poziomu metod w klasach Visual Basic .NET. Visual Basic 6.0 i starszych wersji niejawnie tworzy wystąpienia takich obiektów, należy wywołać metod ich po raz pierwszy. Na przykład w Visual Basic 6.0 można dodać odwołanie do biblioteki obiektów Microsoft DAO 3,6 i wywołanie `DBEngine` metody bez tworzenia wystąpienia:  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic .NET wymaga zawsze twórz wystąpienia obiektów COM przed użyciem ich metod. Aby korzystać z tych metod w języku Visual Basic, zadeklarować zmiennej odpowiednią klasę i użyj słowa kluczowego nowe można przypisać obiektu zmiennej obiektu. `Shared` — Słowo kluczowe może służyć, jeśli chcesz upewnić się, że tylko jedno wystąpienie klasy jest tworzone.  
  
 [!code-vb[VbVbalrInterop#23](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_3.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor9"></a> Nieobsługiwane błędy w obsłudze zdarzeń  
 Jednym z typowych problemów międzyoperacyjnego obejmuje błędy w obsłudze zdarzenia, które obsługi zdarzenia generowane przez obiekty COM. Takie błędy są ignorowane w szczególności należy sprawdzić błędy, używając `On Error` lub `Try...Catch...Finally` instrukcje. Na przykład poniższy przykład pochodzi z projektu programu Visual Basic .NET, który zawiera odwołanie do obiektu Microsoft ActiveX danych obiektów 2.8 biblioteki COM.  
  
 [!code-vb[VbVbalrInterop#24](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_4.vb)]  
  
 W tym przykładzie zgłasza błąd, zgodnie z oczekiwaniami. Jednak Jeśli spróbujesz tym samym przykładzie bez `Try...Catch...Finally` bloku, błąd jest ignorowany, jak w przypadku korzystania `OnError Resume Next` instrukcji. Brak obsługi błędów dzielenie przez zero dyskretnie nie powiedzie się. Ponieważ takie błędy nigdy nie Zgłoś błędy nieobsługiwany wyjątek, ważne jest użycie jakiegoś obsługi wyjątków w obsługi zdarzeń z obiektami COM procedury obsługi zdarzeń.  
  
### <a name="understanding-com-interop-errors"></a>Opis COM interop błędów  
 Bez obsługi błędów wywołania międzyoperacyjnego często generowanie błędów, które zapewniają niewielka ilość informacji. Jeśli to możliwe, należy użyć strukturalnych obsługi zapewniające więcej informacji na temat problemów podczas występowania błędów. Może to być szczególnie przydatne podczas debugowania aplikacji. Na przykład:  
  
 [!code-vb[VbVbalrInterop#25](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_5.vb)]  
  
 Informacje, takie jak opis błędu HRESULT i źródła COM błędów można znaleźć, sprawdzając zawartość obiektu wyjątku.  
  
##  <a name="vbconinteroperabilitymarshalinganchor10"></a> Problemy z formantu ActiveX  
 Większość formantów ActiveX, które współpracują z Visual Basic 6.0 pracować z Visual Basic .NET bez problemów. Główne wyjątki są kontrole kontenerów lub kontrolki, które wizualnie zawierają inne formanty. Przykłady starsze formantów, które nie działają prawidłowo z programem Visual Studio są następujące:  
  
-   Formant Microsoft Forms 2.0 ramki  
  
-   Formantu góra-dół, znanej także jako pokrętła  
  
-   Sheridan formantu karty  
  
 Istnieje tylko kilka obejścia nieobsługiwany problemów formantu ActiveX. Można przeprowadzić migrację istniejących formantów do programu Visual Studio, jeśli oryginalny kod źródłowy. W przeciwnym razie możesz skontaktować się z dostawcami oprogramowania dla aktualizacji. NET zgodnej wersji formantów, aby zastąpić nieobsługiwane formantów ActiveX.  
  
##  <a name="vbconinteroperabilitymarshalinganchor11"></a> Właściwości tylko do odczytu przekazywanie ByRef formantów  
 Visual Basic .NET czasami zgłasza błędy COM, takie jak "CTL_E_SETNOTSUPPORTED 0x800A017F błąd", podczas przekazywania `ReadOnly` właściwości niektóre starsze formantów ActiveX jako `ByRef` parametrów do innych procedur. Podobne wywołań procedur w języku Visual Basic 6.0 Nie wywołuj błąd, a parametry są traktowane jako przekazany przez wartość. Komunikat o błędzie w języku Visual Basic .NET wskazuje, czy chcesz zmienić właściwość, która nie ma właściwości `Set` procedury.  
  
 Jeśli masz dostęp do procedury wywoływanej można uniknąć tego błędu przy użyciu `ByVal` — słowo kluczowe, aby zadeklarować parametrów, które akceptują `ReadOnly` właściwości. Na przykład:  
  
 [!code-vb[VbVbalrInterop#26](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_6.vb)]  
  
 Jeśli nie masz dostępu do kodu źródłowego dla procedury wywoływanej, możesz wymusić właściwości przekazywany przez wartość przez dodanie dodatkowych zbiór nawiasy wywołanie procedury. Na przykład w projekcie, które zawiera odwołanie do obiektu Microsoft ActiveX danych obiektów 2.8 biblioteki COM, można:  
  
 [!code-vb[VbVbalrInterop#27](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_7.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor12"></a> Wdrażanie zestawów, które udostępniają Interop  
 Wdrażanie zestawów, które udostępniają interfejsy modelu COM przedstawia niektóre wyjątkowe wyzwanie. Na przykład potencjalny problem występuje, gdy aplikacje oddzielne odwoływać się do tego samego zestawu COM. Ta sytuacja jest wspólne, gdy instalowana jest nowa wersja zestawu i starą wersję zestawu nadal jest używany przez inną aplikację. Po odinstalowaniu zestawu, który udostępnia bibliotekę DLL, użytkownik może przypadkowo był dostępny dla innych zestawów.  
  
 Aby uniknąć tego problemu, należy zainstalować udostępnionych zestawów do globalnej pamięci podręcznej zestawów (GAC) i użycia dla składowej MergeModule. Jeśli nie można zainstalować aplikacji w pamięci podręcznej GAC, należy zainstalować na CommonFilesFolder w podkatalogu określonej wersji.  
  
 Zestawy, które nie są udostępnione powinien znajdować się obok siebie w katalogu z aplikacji wywołującej.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tlbimp.exe (importer biblioteki typów)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (eksporter biblioteki typów)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Przewodnik: wdrażanie dziedziczenia z obiektami COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Inherits, instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Global Assembly Cache](../../../framework/app-domains/gac.md)
