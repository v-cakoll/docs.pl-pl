---
title: Rozwiązywanie problemów związanych z współdziałaniem
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
ms.openlocfilehash: 344c180cf0b9426898e17b45db768a337fd45beb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74338687"
---
# <a name="troubleshooting-interoperability-visual-basic"></a>Rozwiązywanie problemów związanych z współdziałaniem (Visual Basic)
Podczas współdziałania między modelem COM i zarządzanym kodem .NET Framework mogą wystąpić następujące typowe problemy.  
  
## <a name="vbconinteroperabilitymarshalinganchor1"></a>Organizowanie międzyoperacyjnych  
 Czasami może być konieczne użycie typów danych, które nie są częścią .NET Framework. Zestawy międzyoperacyjności obsługują większość pracy dla obiektów COM, ale może być konieczne kontrolowanie typów danych, które są używane, gdy obiekty zarządzane są udostępniane modelowi COM. Na przykład struktury w bibliotekach klas muszą określać `BStr` typ niezarządzany dla ciągów wysyłanych do obiektów COM utworzonych przez Visual Basic 6,0 i wcześniejszych wersjach. W takich przypadkach można użyć atrybutu <xref:System.Runtime.InteropServices.MarshalAsAttribute>, aby spowodować, że typy zarządzane mają być ujawnione jako typy niezarządzane.  
  
## <a name="vbconinteroperabilitymarshalinganchor2"></a>Eksportowanie ciągów o stałej długości do kodu niezarządzanego  
 W Visual Basic 6,0 i wcześniejszych wersjach ciągi są eksportowane do obiektów COM jako sekwencje bajtów bez znaku zakończenia null. W celu zapewnienia zgodności z innymi językami Visual Basic .NET zawiera znak zakończenia podczas eksportowania ciągów. Najlepszym sposobem na rozwiązanie tej niezgodności jest wyeksportowanie ciągów, które nie mają znaku zakończenia jako tablic `Byte` lub `Char`.  
  
## <a name="vbconinteroperabilitymarshalinganchor3"></a>Eksportowanie hierarchii dziedziczenia  
 Zarządzane hierarchie klas są spłaszczane, gdy są udostępniane jako obiekty COM. Na przykład, jeśli zdefiniujesz klasę bazową z elementem członkowskim, a następnie odziedziczysz klasę bazową w klasie pochodnej, która jest udostępniona jako obiekt COM, klienci korzystający z klasy pochodnej w obiekcie COM nie będą mogli korzystać z dziedziczonych elementów członkowskich. Elementy członkowskie klasy bazowej są dostępne z obiektów COM tylko jako wystąpienia klasy bazowej, a następnie tylko wtedy, gdy klasa podstawowa jest również tworzona jako obiekt COM.  
  
## <a name="overloaded-methods"></a>Przeciążone metody  
 Chociaż można tworzyć przeciążone metody za pomocą Visual Basic, nie są one obsługiwane przez model COM. Gdy Klasa, która zawiera przeciążone metody jest ujawniona jako obiekt COM, nowe nazwy metod są generowane dla przeciążonych metod.  
  
 Rozważmy na przykład klasę, która ma dwa przeciążenia metody `Synch`. Po udostępnieniu klasy jako obiektu COM nowe nazwy metod mogą być `Synch` i `Synch_2`.  
  
 Zmiana nazwy może spowodować dwa problemy dla klientów obiektu COM.  
  
1. Klienci mogą nie oczekiwać wygenerowanych nazw metod.  
  
2. Nazwy wygenerowanej metody w klasie uwidocznionej jako obiekt COM mogą ulec zmianie, gdy nowe przeciążenia są dodawane do klasy lub jej klasy bazowej. Może to spowodować problemy z przechowywaniem wersji.  
  
 Aby rozwiązać oba problemy, nadaj każdej metodzie unikatową nazwę, zamiast używać przeciążenia, podczas tworzenia obiektów, które będą udostępniane jako obiekty COM.  
  
## <a name="vbconinteroperabilitymarshalinganchor4"></a>Korzystanie z obiektów COM za pomocą zestawów międzyoperacyjnych  
 Zestawy międzyoperacyjności są używane prawie tak, jakby były zamiennikami kodu zarządzanego dla obiektów COM, które reprezentują. Jednak ponieważ są to otoki i nierzeczywiste obiekty COM, istnieją pewne różnice między różnymi zestawami międzyoperacyjnymi i zestawami standardowymi. Te obszary różnic obejmują narażenie klas i typy danych dla parametrów i zwracanych wartości.  
  
## <a name="vbconinteroperabilitymarshalinganchor5"></a>Klasy uwidocznione jako interfejsy i klasy  
 W przeciwieństwie do klas w zestawach standardowych klasy COM są ujawniane w zestawach międzyoperacyjnych jako interfejs i Klasa, która reprezentuje klasę COM. Nazwa interfejsu jest taka sama jak w przypadku klasy COM. Nazwa klasy międzyoperacyjnego jest taka sama jak w przypadku oryginalnej klasy COM, ale z dołączonym słowem "Class". Załóżmy na przykład, że masz projekt z odwołaniem do zestawu międzyoperacyjnego dla obiektu COM. Jeśli Klasa COM ma nazwę `MyComClass`, funkcja IntelliSense i Przeglądarka obiektów pokazują interfejs o nazwie `MyComClass` oraz klasę o nazwie `MyComClassClass`.  
  
## <a name="vbconinteroperabilitymarshalinganchor6"></a>Tworzenie wystąpień klasy .NET Framework  
 Ogólnie rzecz biorąc tworzysz wystąpienie klasy .NET Framework przy użyciu instrukcji `New` z nazwą klasy. Posiadanie klasy COM reprezentowanej przez zestaw międzyoperacyjny jest w jednym przypadku, w którym można użyć instrukcji `New` z interfejsem. Jeśli nie korzystasz z klasy COM z instrukcją `Inherits`, możesz użyć interfejsu tak samo jak w przypadku klasy. Poniższy kod ilustruje sposób tworzenia obiektu `Command` w projekcie, który ma odwołanie do obiektu COM biblioteki Microsoft ActiveX Data Objects 2,8:  
  
 [!code-vb[VbVbalrInterop#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#20)]  
  
 Jeśli jednak korzystasz z klasy COM jako podstawy dla klasy pochodnej, musisz użyć klasy międzyoperacyjności, która reprezentuje klasę COM, jak w poniższym kodzie:  
  
 [!code-vb[VbVbalrInterop#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#21)]  
  
> [!NOTE]
> Zestawy międzyoperacyjności niejawnie implementują interfejsy reprezentujące klasy COM. Nie należy próbować używać instrukcji `Implements`, aby zaimplementować te interfejsy lub wystąpił błąd.  
  
## <a name="vbconinteroperabilitymarshalinganchor7"></a>Typy danych dla parametrów i zwracanych wartości  
 W przeciwieństwie do elementów członkowskich zestawów standardowych, składowe zestawu międzyoperacyjnego mogą mieć różne typy danych, które różnią się od tych używanych w deklaracji oryginalnego obiektu. Chociaż zestawy międzyoperacyjności niejawnie konwertują typy COM na zgodne typy środowiska uruchomieniowego języka wspólnego, należy zwrócić uwagę na typy danych, które są używane przez obie strony, aby zapobiec błędom środowiska uruchomieniowego. Na przykład w obiektach COM utworzonych w Visual Basic 6,0 i wcześniejszych wersjach wartości typu `Integer` przyjmuje .NET Framework odpowiedni typ `Short`. Zaleca się użycie Przeglądarka obiektów do badania cech zaimportowanych elementów członkowskich przed ich użyciem.  
  
## <a name="vbconinteroperabilitymarshalinganchor8"></a>Metody COM na poziomie modułu  
 Większość obiektów COM jest używana przez utworzenie wystąpienia klasy COM przy użyciu słowa kluczowego `New`, a następnie wywołanie metod obiektu. Jeden wyjątek od tej reguły obejmuje obiekty COM, które zawierają klasy `AppObj` lub `GlobalMultiUse` COM. Takie klasy przypominają metody poziomu modułu w Visual Basic klas .NET. Visual Basic 6,0 i wcześniejsze wersje niejawnie tworzą wystąpienia takich obiektów przy pierwszym wywołaniu jednej z metod. Na przykład w Visual Basic 6,0 można dodać odwołanie do biblioteki obiektów Microsoft DAO 3,6 i wywołać metodę `DBEngine` bez wcześniejszego tworzenia wystąpienia:  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic .NET wymaga, aby zawsze tworzyć wystąpienia obiektów COM przed użyciem ich metod. Aby użyć tych metod w Visual Basic, zadeklaruj zmienną żądanej klasy i użyj słowa kluczowego new, aby przypisać obiekt do zmiennej obiektu. Słowa kluczowego `Shared` można użyć, aby upewnić się, że tworzone jest tylko jedno wystąpienie klasy.  
  
 [!code-vb[VbVbalrInterop#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#23)]  
  
## <a name="vbconinteroperabilitymarshalinganchor9"></a>Nieobsłużone błędy w obsłudze zdarzeń  
 Jeden z typowych problemów międzyoperacyjnych obejmuje błędy w obsłudze zdarzeń, które obsługują zdarzenia wywoływane przez obiekty COM. Takie błędy są ignorowane, chyba że sprawdzisz błędy przy użyciu instrukcji `On Error` lub `Try...Catch...Finally`. Na przykład poniższy przykład pochodzi z projektu programu .NET Visual Basic, który ma odwołanie do obiektu COM biblioteki Microsoft ActiveX Data Objects 2,8.  
  
 [!code-vb[VbVbalrInterop#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#24)]  
  
 Ten przykład wywołuje błąd zgodnie z oczekiwaniami. Jednak jeśli spróbujesz użyć tego samego przykładu bez bloku `Try...Catch...Finally`, błąd zostanie zignorowany tak, jakby użyto instrukcji `OnError Resume Next`. Bez obsługi błędów, oddzielenie przez zero dyskretnie kończy się niepowodzeniem. Ponieważ takie błędy nigdy nie zgłaszają nieobsłużonych błędów wyjątków, ważne jest, aby użyć pewnej formy obsługi wyjątków w procedurach obsługi zdarzeń, które obsługują zdarzenia z obiektów COM.  
  
### <a name="understanding-com-interop-errors"></a>Omówienie błędów międzyoperacyjnych modelu COM  
 Bez obsługi błędów wywołania międzyoperacyjności często generują błędy, które zawierają niewiele informacji. Jeśli to możliwe, użyj obsługi błędów strukturalnych, aby uzyskać więcej informacji o problemach, gdy wystąpią. Może to być szczególnie przydatne podczas debugowania aplikacji. Na przykład:  
  
 [!code-vb[VbVbalrInterop#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#25)]  
  
 Informacje takie jak opis błędu, HRESULT i źródło błędów COM można znaleźć, sprawdzając zawartość obiektu Exception.  
  
## <a name="vbconinteroperabilitymarshalinganchor10"></a>Problemy z kontrolką ActiveX  
 Większość formantów ActiveX, które działają z Visual Basic 6,0 współpracuje z Visual Basic .NET bez problemów. Główne wyjątki są kontrolkami kontenera lub kontrolki, które wizualnie zawierają inne kontrolki. Przykłady starszych formantów, które nie działają poprawnie z programem Visual Studio, są następujące:  
  
- Kontrolka ramki 2,0 programu Microsoft Forms  
  
- Kontrolka w górę, nazywana również kontrolką pokrętła  
  
- Kontrolka karta Sheridan  
  
 Istnieje tylko kilka obejść problemów z nieobsługiwanymi formantami ActiveX. Istnieje możliwość migrowania istniejących formantów do programu Visual Studio, jeśli jesteś właocicielem oryginalnego kodu źródłowego. W przeciwnym razie można skontaktować się z dostawcami oprogramowania w celu zaktualizowania. Zgodne z SIECIami wersje formantów do zastępowania nieobsługiwanych kontrolek ActiveX.  
  
## <a name="vbconinteroperabilitymarshalinganchor11"></a>Przekazywanie właściwości ReadOnly formantów ByRef  
 Visual Basic .NET czasami wywołuje błędy COM, takie jak "Error 0x800A017F CTL_E_SETNOTSUPPORTED", po przejściu `ReadOnly` właściwości niektórych starszych kontrolek ActiveX jako parametrów `ByRef` do innych procedur. Podobne wywołania procedur z Visual Basic 6,0 nie zgłaszają błędu, a parametry są traktowane tak, jakby były przenoszone przez wartość. Komunikat o błędzie Visual Basic .NET wskazuje, że próbujesz zmienić właściwość, która nie ma właściwości `Set`.  
  
 Jeśli masz dostęp do wywoływanej procedury, możesz uniknąć tego błędu, używając słowa kluczowego `ByVal`, aby zadeklarować parametry, które akceptują `ReadOnly` właściwości. Na przykład:  
  
 [!code-vb[VbVbalrInterop#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#26)]  
  
 Jeśli nie masz dostępu do kodu źródłowego dla wywoływanej procedury, możesz wymusić, aby właściwość została przeniesiona przez wartość przez dodanie dodatkowego zestawu nawiasów wokół procedury wywołującej. Na przykład w projekcie, który ma odwołanie do obiektu COM biblioteki Microsoft ActiveX Data Objects 2,8, można użyć:  
  
 [!code-vb[VbVbalrInterop#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#27)]  
  
## <a name="vbconinteroperabilitymarshalinganchor12"></a>Wdrażanie zestawów, które uwidaczniają międzyoperacyjność  
 Wdrożenie zestawów, które uwidacznia interfejsy COM, stanowi pewne unikatowe wyzwania. Na przykład potencjalny problem występuje, gdy oddzielne aplikacje odwołują się do tego samego zestawu COM. Ta sytuacja jest powszechna, gdy jest zainstalowana nowa wersja zestawu, a inna aplikacja nadal używa starej wersji zestawu. W przypadku odinstalowania zestawu, który udostępnia bibliotekę DLL, można przypadkowo uniemożliwić jej dostęp do innych zestawów.  
  
 Aby uniknąć tego problemu, należy zainstalować zestawy udostępnione w globalnej pamięci podręcznej zestawów (GAC) i użyć elementu MergeModule dla składnika. Jeśli nie można zainstalować aplikacji w pamięci podręcznej GAC, należy ją zainstalować, aby CommonFilesFolder w podkatalogu specyficznym dla wersji.  
  
 Zestawy, które nie są udostępniane, powinny znajdować się obok siebie w katalogu za pomocą aplikacji wywołującej.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Tlbimp.exe (importer biblioteki typów)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (eksporter biblioteki typów)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Przewodnik: wdrażanie dziedziczenia z obiektami COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Inherits, instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Global Assembly Cache](../../../framework/app-domains/gac.md)
