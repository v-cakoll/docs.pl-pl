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
ms.openlocfilehash: 147c61badd680277480226b809df97d46b636c7d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341195"
---
# <a name="troubleshooting-interoperability-visual-basic"></a>Rozwiązywanie problemów związanych z współdziałaniem (Visual Basic)
Gdy współdziałania między COM i kodu zarządzanego z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], może wystąpić co najmniej jeden z następujących typowych problemów.  
  
## <a name="vbconinteroperabilitymarshalinganchor1"></a> Marshaling międzyoperacyjny  
 Czasami może być używanie typów danych, które nie są częścią [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Zestawy międzyoperacyjne obsługiwać większość pracy dla obiektów COM, ale może być konieczne kontrolować typów danych, które są używane, gdy zarządzane obiekty są widoczne dla modelu COM. Na przykład, należy określić struktur w bibliotekach klas `BStr` niezarządzany typ na ciągi wysyłana do obiektów COM, utworzone przez program Visual Basic 6.0 i starszych wersji. W takich przypadkach można użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu, aby spowodować, że typy zarządzane ujawnianie jako typy niezarządzanych.  
  
## <a name="vbconinteroperabilitymarshalinganchor2"></a> Eksportowanie ciągi o stałej długości do kodu niezarządzanego  
 W Visual Basic 6.0 i starszych wersjach ciągi są eksportowane do obiektów COM jako sekwencje bajtów bez znaku null zakończenie. Zgodność z innymi językami Visual Basic .NET zawiera znak zakończenia, podczas eksportowania ciągów. Najlepszym sposobem rozwiązania ta niezgodność nie jest eksportowane ciągów, które nie mają znak zakończenia jako tablice tego `Byte` lub `Char`.  
  
## <a name="vbconinteroperabilitymarshalinganchor3"></a> Eksportowanie hierarchii dziedziczenia  
 Zarządzane klasy, która hierarchii, spłaszczenie się ujawniane jako obiekty COM. Na przykład jeśli zdefiniować klasę bazową z elementem członkowskim, a następnie dziedziczyć klasy podstawowej w klasie pochodnej, która jest widoczna jako obiekt COM, klientów, którzy używają klasy pochodnej w obiekcie COM nie będzie używać dziedziczone elementy członkowskie. Składowych klasy bazowej są dostępne z obiektami COM tylko jako wystąpienia klasy bazowej, a następnie tylko wtedy, gdy klasa bazowa jest tworzona jako obiekt COM.  
  
## <a name="overloaded-methods"></a>Przeciążone metody  
 Chociaż przeciążonych metod można tworzyć za pomocą Visual Basic, nie są obsługiwane przez model COM. Ujawniane klasę, która zawiera przeciążonych metod jako obiekt COM nowe nazwy metody są generowane dla przeciążonych metod.  
  
 Rozważmy na przykład klasa, która ma dwa przeciążenia metody `Synch` metody. Gdy klasa jest udostępniana jako obiekt COM, nowe nazwy wygenerowana metoda może być `Synch` i `Synch_2`.  
  
 Zmiana nazwy może spowodować dwa problemy w konsumentach napisanych obiektu COM.  
  
1. Klienci mogą nie oczekuje nazwy wygenerowanej metody.  
  
2. Nazwy wygenerowanej metody w klasie widoczne jako obiekt COM można zmienić, gdy nowe przeciążenia są dodawane do klasy lub jej klasy bazowej. Może to spowodować problemy z wersjonowaniem.  
  
 Aby rozwiązać problemy z obu, nadaj każdej metodzie unikatową nazwę, a nie za pomocą przeciążenia, podczas tworzenia obiektów, które będą dostępne jako obiekty COM.  
  
## <a name="vbconinteroperabilitymarshalinganchor4"></a> Korzystanie z obiektów COM, przy użyciu zestawów międzyoperacyjnych  
 Możesz użyć usług międzyoperacyjnych prawie tak, jakby były zamiany kodu zarządzanego dla obiektów COM, które reprezentują. Jednakże ponieważ są one otoki, a nie rzeczywiste obiektów COM, istnieją pewne różnice między przy użyciu zestawów międzyoperacyjnych i standardowe zestawy. Te obszary różnicy to narażenie klas i typów danych parametrów i zwracanych wartości.  
  
## <a name="vbconinteroperabilitymarshalinganchor5"></a> Klasy widoczne jako dotyczą obu interfejsów i klasy  
 W odróżnieniu od klas w standardowe zestawy klasy COM są widoczne w zestawach międzyoperacyjnych jako interfejs i klasę, która reprezentuje klasę modelu COM. Nazwa interfejsu jest taka sama jak w przypadku klasy COM. Nazwa klasy międzyoperacyjny jest taka sama, jak w przypadku oryginalnej klasy COM, ale wyrazem "Class" jest dołączona. Na przykład załóżmy, że masz projekt za pomocą odwołania do zestawu międzyoperacyjnego dla obiektu COM. Jeśli klasa COM nosi nazwę `MyComClass`, funkcja IntelliSense i przeglądarki obiektów pokazać interfejs o nazwie `MyComClass` i klasę o nazwie `MyComClassClass`.  
  
## <a name="vbconinteroperabilitymarshalinganchor6"></a> Tworzenie wystąpienia klasy .NET Framework  
 Ogólnie rzecz biorąc, Utwórz wystąpienie [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] przy użyciu `New` instrukcję, określając nazwę klasy. Klasa COM, reprezentowane przez zestaw międzyoperacyjny jest jeden przypadek, w którym można użyć `New` instrukcji przy użyciu interfejsu. Jeśli nie używasz klasy COM za pomocą `Inherits` instrukcji, tak samo jak klasy, można użyć interfejsu. Poniższy kod przedstawia sposób tworzenia `Command` obiektu w projekcie, który zawiera odwołanie do obiektu ActiveX firmy Microsoft danych 2.8 obiektów biblioteki modelu COM:  
  
 [!code-vb[VbVbalrInterop#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#20)]  
  
 Jednak jeśli używasz klasy modelu COM jako podstawy dla klasy pochodnej, należy użyć międzyoperacyjny klasę, która reprezentuje klasę modelu COM, zgodnie z poniższym kodem:  
  
 [!code-vb[VbVbalrInterop#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#21)]  
  
> [!NOTE]
>  Zestawy międzyoperacyjne niejawnie implementować interfejsy, które reprezentują klasy COM. Nie należy próbować użyć `Implements` spowoduje instrukcję, aby zaimplementować te interfejsy lub komunikat o błędzie.  
  
## <a name="vbconinteroperabilitymarshalinganchor7"></a> Typy danych dla parametrów i zwracanych wartości  
 W odróżnieniu od członków standardowe zestawy zestaw międzyoperacyjny członkowie mogą mieć typów danych, które różnią się od tych używanych w oryginalnej deklaracji obiektu. Mimo że zestawy międzyoperacyjne niejawnie przekonwertować typy modelu COM zgodnych typów środowiska wykonawczego języka wspólnego, należy zwrócić uwagę na typy danych, które są używane przez obie strony, aby zapobiec wystąpieniu błędów środowiska uruchomieniowego. Na przykład w przypadku obiektów COM, utworzone w języku Visual Basic 6.0 i starsze wersje, wartości typu `Integer` założono [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] równoważny typ `Short`. Zalecane jest, użyj przeglądarki obiektów do zbadania właściwości elementów członkowskich zaimportowane przed ich użyciem.  
  
## <a name="vbconinteroperabilitymarshalinganchor8"></a> Moduł metod na poziomie modelu COM  
 Większość obiektów COM są używane przez utworzenie wystąpienia klasy modelu COM za pomocą `New` — słowo kluczowe, a następnie wywoływania metod obiektu. Jedynym wyjątkiem od tej reguły pociąga za sobą obiektów COM, które zawierają `AppObj` lub `GlobalMultiUse` klasy COM. Takich klas przypominają modułu poziomu metod w klasach Visual Basic .NET. Visual Basic 6.0 i starsze wersje niejawnie tworzy wystąpienia takich obiektów, należy wywołać metody ich po raz pierwszy. Na przykład w języku Visual Basic 6.0 można dodać odwołanie do biblioteki obiektów Microsoft DAO 3.6 i wywołanie `DBEngine` metody bez tworzenia wystąpienia:  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic .NET wymaga zawsze tworzenia wystąpień obiektów COM przed użyciem ich metod. Aby korzystać z tych metod w języku Visual Basic, Zadeklaruj zmienną odpowiednią klasę i użyj słowa kluczowego new, aby przypisać obiekt do zmiennej obiektu. `Shared` — Słowo kluczowe może służyć, jeśli chcesz upewnić się, że tylko jedno wystąpienie tej klasy jest tworzona.  
  
 [!code-vb[VbVbalrInterop#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#23)]  
  
## <a name="vbconinteroperabilitymarshalinganchor9"></a> Nieobsługiwane błędy w obsłudze zdarzeń  
 Jednym z typowych problemów międzyoperacyjny polega na błędy w procedurze obsługi zdarzeń, obsługujące zdarzenia generowane przez obiekty COM. Takie błędy są ignorowane, chyba że specjalnie sprawdzania błędów przy użyciu `On Error` lub `Try...Catch...Finally` instrukcji. Na przykład poniższy przykład pochodzi z projektu języka Visual Basic .NET, który zawiera odwołanie do obiektu ActiveX firmy Microsoft danych 2.8 obiektów biblioteki modelu COM.  
  
 [!code-vb[VbVbalrInterop#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#24)]  
  
 W tym przykładzie zgłasza błąd, zgodnie z oczekiwaniami. Jednak jeśli zostanie podjęta w tym samym przykładzie bez `Try...Catch...Finally` bloku, błąd jest ignorowany, jak w przypadku korzystania `OnError Resume Next` instrukcji. Bez obsługi błędów, dzielenie przez zero dyskretnie kończy się niepowodzeniem. Ponieważ takie błędy nigdy nie zgłaszać błędy nieobsługiwany wyjątek, jest ważne, że używasz pewnego rodzaju obsługi wyjątków w procedury obsługi zdarzeń, które obsługują zdarzenia z obiektami COM.  
  
### <a name="understanding-com-interop-errors"></a>Informacje o błędach międzyoperacyjnego modelu COM  
 Bez obsługi błędów wywołań międzyoperacyjnych często generować błędy, które zapewniają trochę informacji. Możliwe, używaj ze strukturą obsługę błędów do Podaj więcej informacji na temat problemów, kiedy się pojawią. Może to być szczególnie przydatne podczas debugowania aplikacji. Na przykład:  
  
 [!code-vb[VbVbalrInterop#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#25)]  
  
 Informacje, takie jak opis błędu HRESULT i źródłem błędów COM można znaleźć, sprawdzając zawartość obiektu wyjątku.  
  
## <a name="vbconinteroperabilitymarshalinganchor10"></a> Problemy z kontrolki ActiveX  
 Większość kontrolki ActiveX, współpracujących z Visual Basic 6.0 pracować w Visual Basic .NET, które bez problemów. Główne wyjątki są kontrole kontenerów lub formanty, które będzie zawierać inne kontrolki. Kilka przykładów starsze formantów, które nie będą działać poprawnie z programem Visual Studio są następujące:  
  
-   Formant programu Microsoft Forms 2.0 ramki  
  
-   Góra-dół kontrolki, znany także jako kontrolki pokrętła  
  
-   Kontrolka karty Sheridan  
  
 Istnieją tylko kilka obejścia nieobsługiwany występują problemy z kontrolki ActiveX. Można przeprowadzić migrację istniejących kontrolek do programu Visual Studio, jeśli jesteś właścicielem oryginalnego kodu źródłowego. W przeciwnym razie możesz skontaktować się z dostawcami oprogramowania dla aktualizacji. NET zgodnej wersji formantów, aby zastąpić nieobsługiwane formanty ActiveX.  
  
## <a name="vbconinteroperabilitymarshalinganchor11"></a> Przekazywanie tylko do odczytu właściwości formantów ByRef  
 Jeśli przekazujesz Visual Basic .NET czasami zgłasza błędy COM, takie jak "Błąd 0x800A017F CTL_E_SETNOTSUPPORTED" `ReadOnly` właściwości niektóre starsze formanty ActiveX jako `ByRef` parametry do innych procedur. Podobnie w przypadku wywołania procedur z Visual Basic 6.0 nie zgłaszaj błąd, a parametry są traktowane tak, jakby przekazywane przez wartość. Komunikat o błędzie Visual Basic .NET wskazuje na to, czy chcesz zmienić właściwość, która nie ma właściwości `Set` procedury.  
  
 Jeśli masz dostęp do procedury wywoływana, możesz uniknąć tego błędu, za pomocą `ByVal` — słowo kluczowe do deklarowania parametry, które akceptują `ReadOnly` właściwości. Na przykład:  
  
 [!code-vb[VbVbalrInterop#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#26)]  
  
 Jeśli nie masz dostępu do kodu źródłowego dla procedury wywoływana, możesz wymusić właściwości, które mają być przekazane przez wartość, dodając dodatkowy zestaw nawiasów wokół procedury wywołującej. Na przykład w projekcie, który zawiera odwołanie do obiektu ActiveX firmy Microsoft danych 2.8 obiektów biblioteki modelu COM, należy użyć:  
  
 [!code-vb[VbVbalrInterop#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#27)]  
  
## <a name="vbconinteroperabilitymarshalinganchor12"></a> Wdrażanie zestawów, które uwidaczniają międzyoperacyjności  
 Wdrażanie zestawów, które uwidaczniają interfejsów COM przedstawiono niektóre wyzwania. Na przykład potencjalny problem występuje, gdy aplikacje oddzielne odwoływać się do tego samego zestawu COM. Ta sytuacja jest typowa, gdy nowa wersja zestawu jest zainstalowany i starą wersję zestawu nadal jest używany przez inną aplikację. Po odinstalowaniu zestawu, który udostępnia bibliotekę DLL, użytkownik może przypadkowo był dostępny dla innych zestawów.  
  
 Aby uniknąć tego problemu, możesz zainstalować współużytkowanych zestawów do globalnej pamięci podręcznej zestawów (GAC) i użyj MergeModule dla składnika. Jeśli aplikacja nie można zainstalować w GAC, powinien być zainstalowany na CommonFilesFolder w podkatalogu specyficzny dla wersji.  
  
 Zestawy, które nie są współdzielone powinny się znajdować obok siebie w katalogu z aplikacji wywołującej.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)
- [Tlbimp.exe (Importer biblioteki typów)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (Eksporter biblioteki typów)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Przewodnik: Wdrażanie dziedziczenia z obiektami COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Inherits — Instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Global Assembly Cache](../../../framework/app-domains/gac.md)
