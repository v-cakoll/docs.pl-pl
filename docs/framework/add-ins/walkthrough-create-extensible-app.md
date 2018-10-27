---
title: 'Wskazówki: tworzenie aplikacji rozszerzalnej'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [.NET Framework], add-in pipeline
- host-side adapters for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], creating
- add-in-side adapter [.NET Framework]
- contracts for add-in pipelines [.NET Framework]
ms.assetid: 694a33c5-a040-450d-aed5-ac49fc88ce61
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63780583d035d6fab6b3a79424857b82a910ef09
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183896"
---
# <a name="walkthrough-creating-an-extensible-application"></a>Wskazówki: tworzenie aplikacji rozszerzalnej
W tym przewodniku opisano tworzenie potoku dodatku, który wykonuje funkcje prosty kalkulator. Nie przedstawiono tu rzeczywistych scenariuszy; zamiast pokazuje podstawową funkcjonalność potoku i jak dodatek mogą udostępniać usługi hosta.  
  
 W tym przewodniku opisano następujące zadania:  
  
-   Tworzenie rozwiązania programu Visual Studio.  
  
-   Tworzenie struktury katalogów potoku.  
  
-   Tworzenie kontraktu i widoków.  
  
-   Tworzenie adaptera add w side.  
  
-   Tworzenie karty po stronie hosta.  
  
-   Tworzenie hosta.  
  
-   Tworzenie dodatku.  
  
-   Wdrażanie potoku.  
  
-   Uruchamianie aplikacji hosta.  
  
 Ten potok przekazuje tylko typów możliwych do serializacji (<xref:System.Double> i <xref:System.String>), między hostem a dodatkiem. Aby uzyskać przykład pokazujący sposób przekazywania kolekcji typów złożonych danych, zobacz [wskazówki: przekazywanie kolekcji między hostami i Add-Ins](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).  
  
 Kontrakt dla tego potoku definiuje model obiektu cztery operacje arytmetyczne: dodawania, odejmowania, mnożenia i dzielenia. Host zapewnia dodatek równania, aby obliczyć, takie jak 2 + 2, i dodatku zwraca wynik do hosta.  
  
 W wersji 2 dodatku Kalkulator zapewnia możliwości bardziej obliczania i przedstawia przechowywanie wersji. Jest on opisany w [przewodnik: Włączanie zgodności z poprzednimi wersjami Your zmian hosta](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebne są następujące czynności w celu przeprowadzenia tego instruktażu:  
  
-   Program Visual Studio.  
  
## <a name="creating-a-visual-studio-solution"></a>Tworzenie rozwiązań programu Visual Studio  
 Zawiera projekty segmentów potoku przy użyciu rozwiązania w programie Visual Studio.  
  
#### <a name="to-create-the-pipeline-solution"></a>Aby utworzyć rozwiązanie potoku  
  
1.  W programie Visual Studio Utwórz nowy projekt o nazwie `Calc1Contract`. Oparte na **biblioteki klas** szablonu.  
  
2.  Nazwij rozwiązanie `CalculatorV1`.  
  
## <a name="creating-the-pipeline-directory-structure"></a>Tworzenie struktury katalogów potoku  
 Model dodatku wymaga zestawy segmentów potoku do umieszczenia w strukturze określonego katalogu. Aby uzyskać więcej informacji na temat struktury potoku, zobacz [wymagania dotyczące opracowywania potoku](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
#### <a name="to-create-the-pipeline-directory-structure"></a>Aby utworzyć potok struktury katalogów  
  
1.  Utwórz folder aplikacji w dowolnym miejscu na komputerze.  
  
2.  W tym folderze utwórz następującą strukturę:  
  
    ```  
    Pipeline  
      AddIns  
        CalcV1  
        CalcV2  
      AddInSideAdapters  
      AddInViews  
      Contracts  
      HostSideAdapters  
    ```  
  
     Nie jest konieczne umieścić potoku strukturę folderów w folderze aplikacji; jest wykonywane tutaj wyłącznie dla wygody. Na etapie odpowiednie przewodnik wyjaśnia, jak zmiany kodu, jeśli struktura folderów potoku znajduje się w innej lokalizacji. Zobacz Omówienie wymagań katalogu potoku w [wymagania dotyczące opracowywania potoku](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
    > [!NOTE]
    >  `CalcV2` Folder nie jest używany w tym przewodniku; jest symbolem zastępczym dla [przewodnik: Włączanie zgodności z poprzednimi wersjami Your zmian hosta](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).  
  
## <a name="creating-the-contract-and-views"></a>Tworzenie kontraktu i widoków  
 Określa segment umowy, dla tego potoku `ICalc1Contract` interfejs, który definiuje cztery metody: `add`, `subtract`, `multiply`, i `divide`.  
  
#### <a name="to-create-the-contract"></a>Aby utworzyć kontrakt  
  
1.  W rozwiązaniu Visual Studio o nazwie `CalculatorV1`, otwórz `Calc1Contract` projektu.  
  
2.  W **Eksploratora rozwiązań**, dodaj odwołania do następujących zestawów, które mają `Calc1Contract` projektu:  
  
     System.AddIn.Contract.dll  
  
     System.AddIn.dll  
  
3.  W **Eksploratora rozwiązań**, Wyklucz domyślnej klasy, który jest dodawany do nowego **biblioteki klas** projektów.  
  
4.  W **Eksploratora rozwiązań**, Dodaj nowy element do projektu, przy użyciu **interfejsu** szablonu. W **Dodaj nowy element** okno dialogowe, nazwa interfejsu `ICalc1Contract`.  
  
5.  W pliku interfejsu, należy dodać odwołania do przestrzeni nazw do <xref:System.AddIn.Contract> i <xref:System.AddIn.Pipeline>.  
  
6.  Użyj poniższego kodu, aby ukończyć ten segment kontraktu. Należy zauważyć, że ten interfejs musi mieć <xref:System.AddIn.Pipeline.AddInContractAttribute> atrybutu.  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  Opcjonalnie można tworzyć rozwiązania programu Visual Studio. Rozwiązania nie można uruchomić, dopóki ostatecznej procedurze, ale wbudowanie jej po każdej procedury gwarantuje, że każdy projekt jest rozwiązać.  
  
 Widok dodatku i host widoku dodatku zazwyczaj mają ten sam kod, szczególnie w pierwszej wersji dodatku, można łatwo utworzyć widoków, w tym samym czasie. Różnią się tylko jeden składnik: widok dodatek wymaga <xref:System.AddIn.Pipeline.AddInBaseAttribute> atrybutu, natomiast widok hosta dodatków nie wymaga żadnych atrybutów.  
  
#### <a name="to-create-the-add-in-view"></a>Aby utworzyć widok dodatku  
  
1.  Dodaj nowy projekt o nazwie `Calc1AddInView` do `CalculatorV1` rozwiązania. Oparte na **biblioteki klas** szablonu.  
  
2.  W **Eksploratora rozwiązań**, Dodaj odwołanie do System.AddIn.dll do `Calc1AddInView` projektu.  
  
3.  W **Eksploratora rozwiązań**, Wyklucz domyślnej klasy, który jest dodawany do nowego **biblioteki klas** projektów i Dodaj nowy element do projektu, przy użyciu **interfejsu** szablonu. W **Dodaj nowy element** okno dialogowe, nazwa interfejsu `ICalculator`.  
  
4.  W pliku interfejsu, Dodaj odwołanie do przestrzeni nazw <xref:System.AddIn.Pipeline>.  
  
5.  Użyj poniższego kodu, aby ukończyć ten widok dodatku. Należy zauważyć, że ten interfejs musi mieć <xref:System.AddIn.Pipeline.AddInBaseAttribute> atrybutu.  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  Opcjonalnie można tworzyć rozwiązania programu Visual Studio.  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a>Aby utworzyć widok hosta dodatków  
  
1.  Dodaj nowy projekt o nazwie `Calc1HVA` do `CalculatorV1` rozwiązania. Oparte na **biblioteki klas** szablonu.  
  
2.  W **Eksploratora rozwiązań**, Wyklucz domyślnej klasy, który jest dodawany do nowego **biblioteki klas** projektów i Dodaj nowy element do projektu, przy użyciu **interfejsu** szablonu. W **Dodaj nowy element** okno dialogowe, nazwa interfejsu `ICalculator`.  
  
3.  W pliku interfejsu użyj następującego kodu, aby ukończyć widok hosta dodatków.  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  Opcjonalnie można tworzyć rozwiązania programu Visual Studio.  
  
## <a name="creating-the-add-in-side-adapter"></a>Tworzenie adaptera dodać strony  
 Ta karta Dodaj stronie składa się z jednej karty kontraktu na widok. Ten segment potoku konwertuje typy w widoku Dodaj umowy.  
  
 W tym potoku dodatku udostępnia usługę na hoście, a typy przepływu z dodatku na hoście. Ponieważ żaden z typów usługi flow z hosta do dodatku, ma zawierać adapter kontraktu na widok po stronie dodatku w tym potoku.  
  
#### <a name="to-create-the-add-in-side-adapter"></a>Aby utworzyć adapter add w side  
  
1.  Dodaj nowy projekt o nazwie `Calc1AddInSideAdapter` do `CalculatorV1` rozwiązania. Oparte na **biblioteki klas** szablonu.  
  
2.  W **Eksploratora rozwiązań**, dodaj odwołania do następujących zestawów, które mają `Calc1AddInSideAdapter` projektu:  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  Dodaj odwołania do projektu do projektów segmentów potoku sąsiadujące:  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  Wybierz odwołanie do każdego projektu, a następnie w **właściwości** ustaw **Kopiuj lokalnie** do **False**. W języku Visual Basic należy używać **odwołania** karcie **właściwości projektu** można ustawić **Kopiuj lokalnie** do **False** dwa projektu odwołania.  
  
5.  Zmień nazwę projektu domyślną klasę `CalculatorViewToContractAddInSideAdapter`.  
  
6.  W pliku klasy należy dodać odwołania do przestrzeni nazw do <xref:System.AddIn.Pipeline>.  
  
7.  W pliku klasy należy dodać odwołania do przestrzeni nazw dla sąsiadujących segmentów: `CalcAddInViews` i `CalculatorContracts`. (W języku Visual Basic są te odwołania do przestrzeni nazw `Calc1AddInView.CalcAddInViews` i `Calc1Contract.CalculatorContracts`, o ile nie wyłączysz domyślne obszary nazw w projektach języka Visual Basic.)  
  
8.  Zastosuj <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atrybutu `CalculatorViewToContractAddInSideAdapter` klasy, aby je zidentyfikować jako karta add w side.  
  
9. Wprowadzić `CalculatorViewToContractAddInSideAdapter` klasa dziedziczy <xref:System.AddIn.Pipeline.ContractBase>, który udostępnia domyślną implementację elementu <xref:System.AddIn.Contract.IContract> interfejs i implementować interfejs kontraktu dla potoku, `ICalc1Contract`.  
  
10. Dodaj Konstruktor publiczny, który akceptuje `ICalculator`, zapisuje go w pamięci podręcznej w pole prywatne i wywołuje konstruktora klasy bazowej.  
  
11. Do zaimplementowania elementów członkowskich `ICalc1Contract`, wystarczy wywołać odpowiednie elementy członkowskie `ICalculator` wystąpienia, który jest przekazywany do konstruktora, a następnie zwracają wyniki. To dostosowuje widoku (`ICalculator`) z umową (`ICalc1Contract`).  
  
     Poniższy kod przedstawia ukończone karty dodać strony.  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. Opcjonalnie można tworzyć rozwiązania programu Visual Studio.  
  
## <a name="creating-the-host-side-adapter"></a>Tworzenie adaptera po stronie hosta  
 Ten adapter po stronie hosta składa się z jednej karty kontraktu na widok. Ten segment dostosowuje się kontraktu na widok hosta dodatków.  
  
 W tym potoku dodatku udostępnia usługę hosta i przepływ typów w dodatku do hosta. Ponieważ żaden z typów usługi flow z hosta do dodatku, ma zawierać adapter kontraktu na widok.  
  
 Aby zaimplementować Zarządzanie okresem istnienia, należy użyć <xref:System.AddIn.Pipeline.ContractHandle> obiekt można dołączyć okres istnienia tokenu do Umowy. Odwołanie do tego dojścia musi przechowywać w kolejności do działania zarządzania okresem istnienia. Po zastosowaniu token nie dodatkowego programowania jest wymagane, ponieważ system dodatku można usuwania obiektów, kiedy są już używane i udostępnić je do wyrzucania elementów bezużytecznych. Aby uzyskać więcej informacji, zobacz [Zarządzanie okresem istnienia](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).  
  
#### <a name="to-create-the-host-side-adapter"></a>Aby utworzyć adapter po stronie hosta  
  
1.  Dodaj nowy projekt o nazwie `Calc1HostSideAdapter` do `CalculatorV1` rozwiązania. Oparte na **biblioteki klas** szablonu.  
  
2.  W **Eksploratora rozwiązań**, dodaj odwołania do następujących zestawów, które mają `Calc1HostSideAdapter` projektu:  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  Dodaj odwołania do projektu do projektów sąsiadujących segmentów:  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  Wybierz odwołanie do każdego projektu, a następnie w **właściwości** ustaw **Kopiuj lokalnie** do **False**. W języku Visual Basic należy używać **odwołania** karcie **właściwości projektu** można ustawić **Kopiuj lokalnie** do **False** dwa projektu odwołania.  
  
5.  Zmień nazwę projektu domyślną klasę `CalculatorContractToViewHostSideAdapter`.  
  
6.  W pliku klasy należy dodać odwołania do przestrzeni nazw do <xref:System.AddIn.Pipeline>.  
  
7.  W pliku klasy należy dodać odwołania do przestrzeni nazw dla sąsiadujących segmentów: `CalcHVAs` i `CalculatorContracts`. (W języku Visual Basic są te odwołania do przestrzeni nazw `Calc1HVA.CalcHVAs` i `Calc1Contract.CalculatorContracts`, o ile nie wyłączysz domyślne obszary nazw w projektach języka Visual Basic.)  
  
8.  Zastosuj <xref:System.AddIn.Pipeline.HostAdapterAttribute> atrybutu `CalculatorContractToViewHostSideAdapter` klasy, aby je zidentyfikować jako segment adaptery po stronie hosta.  
  
9. Wprowadź `CalculatorContractToViewHostSideAdapter` klasa implementuje interfejs, który reprezentuje widok hosta dodatków: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` w języku Visual Basic).  
  
10. Dodaj Konstruktor publiczny, który akceptuje typ kontraktu potoku, `ICalc1Contract`. Konstruktor musi pamięci podręcznej odwołanie do Umowy. Należy także utworzyć i pamięci podręcznej nową <xref:System.AddIn.Pipeline.ContractHandle> dla umowy, aby zarządzać okresem istnienia dodatku.  
  
    > [!IMPORTANT]
    >  <xref:System.AddIn.Pipeline.ContractHandle> Mają kluczowe znaczenie dla zarządzania okresem istnienia. Jeśli nie zostanie utrzymywać odwołania do <xref:System.AddIn.Pipeline.ContractHandle> obiektów, wyrzucanie elementów bezużytecznych będzie go odzyskać, a potoku zostanie zamknięty, gdy program nie oczekuje. Może to prowadzić do błędów, które są trudne do zdiagnozowania, takich jak <xref:System.AppDomainUnloadedException>. Zamknięcie jest normalne etapie w cyklu życia potoku, dlatego nie ma możliwości dla kodu zarządzania okres istnienia wykryć, czy ten warunek występuje błąd.  
  
11. Do zaimplementowania elementów członkowskich `ICalculator`, wystarczy wywołać odpowiednie elementy członkowskie `ICalc1Contract` wystąpienia, który jest przekazywany do konstruktora, a następnie zwracają wyniki. To dostosowuje kontraktu (`ICalc1Contract`) do widoku (`ICalculator`).  
  
     Poniższy kod przedstawia ukończone adapter po stronie hosta.  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. Opcjonalnie można tworzyć rozwiązania programu Visual Studio.  
  
## <a name="creating-the-host"></a>Tworzenie hosta  
 Aplikacja hosta wchodzi w interakcje przy użyciu dodatku za pośrednictwem widoku hosta dodatku. Używa dodatku odnajdywania i aktywacja metod dostarczonych przez <xref:System.AddIn.Hosting.AddInStore> i <xref:System.AddIn.Hosting.AddInToken> klasy, aby wykonać następujące czynności:  
  
-   Aktualizacja pamięci podręcznej informacje o potoku i dodatku.  
  
-   Znajdź dodatki typu widoku hosta `ICalculator`, w katalogu głównym określonej potoku.  
  
-   Monituj użytkownika o określenie, której dodatek do użycia.  
  
-   Aktywuj wybrany dodatek w nowej domenie aplikacji z poziomu zaufania zabezpieczeń określone.  
  
-   Uruchom niestandardowe `RunCalculator` metody, która wywołuje metody w dodatku, określony przez widok hosta dodatków.  
  
#### <a name="to-create-the-host"></a>W celu utworzenia hosta  
  
1.  Dodaj nowy projekt o nazwie `Calc1Host` do `CalculatorV1` rozwiązania. Oparte na **aplikację Konsolową** szablonu.  
  
2.  W **Eksploratora rozwiązań**, Dodaj odwołanie do zestawu System.AddIn.dll `Calc1Host` projektu.  
  
3.  Dodaj odwołanie do `Calc1HVA` projektu. Wybierz odwołanie do projektu, a następnie w **właściwości** ustaw **Kopiuj lokalnie** do **False**. W języku Visual Basic należy używać **odwołania** karcie **właściwości projektu** można ustawić **Kopiuj lokalnie** do **False**.  
  
4.  Zmień nazwę pliku klasy (modułu w języku Visual Basic) `MathHost1`.  
  
5.  W języku Visual Basic należy używać **aplikacji** karcie **właściwości projektu** okno dialogowe, aby ustawić **obiekt początkowy** do **Sub Main**.  
  
6.  W pliku klasę lub moduł, należy dodać odwołanie do przestrzeni nazw <xref:System.AddIn.Hosting>.  
  
7.  W pliku klasę lub moduł, Dodaj odwołanie przestrzeni nazw dla widoku hosta dodatku: `CalcHVAs`. (W języku Visual Basic to odwołanie do przestrzeni nazw jest `Calc1HVA.CalcHVAs`, o ile nie wyłączysz domyślne obszary nazw w projektach języka Visual Basic.)  
  
8.  W **Eksploratora rozwiązań**, wybierz rozwiązanie i **projektu** menu wybierz opcję **właściwości**. W **strony właściwości rozwiązania** okno dialogowe, zestaw **pojedynczy projekt startowy** za ten projekt aplikacji hosta.  
  
9. W pliku klasę lub moduł, użyj <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> metodę, aby zaktualizować pamięć podręczną. Użyj <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> metodę, aby uzyskać kolekcję tokenów oraz <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> metodę, aby aktywować dodatku.  
  
     Poniższy kod przedstawia aplikacji hosta ukończone.  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  Ten kod zakłada, że struktura folderów potoku znajduje się w folderze aplikacji. Jeśli użytkownik znajduje się go innym miejscu, zmień wiersz kodu, który ustawia `addInRoot` zmiennej, tak aby zmienna zawiera ścieżkę do potoku struktury katalogów.  
  
     Kod używa `ChooseCalculator` metody, aby wyświetlić listę tokenów i aby monitować użytkownika o wybranie dodatku. `RunCalculator` Metoda monituje użytkownika o wyrażeń matematycznych prosty, analizuje wyrażeń przy użyciu `Parser` klasy i wyświetla wyniki zwrócone przez dodatek.  
  
10. Opcjonalnie można tworzyć rozwiązania programu Visual Studio.  
  
## <a name="creating-the-add-in"></a>Tworzenie dodatku  
 Dodatek implementuje metody określonej przez widok dodatku. Ten dodatek implementuje `Add`, `Subtract`, `Multiply`, i `Divide` operacje i zwraca wyniki do hosta.  
  
#### <a name="to-create-the-add-in"></a>Aby utworzyć dodatek  
  
1.  Dodaj nowy projekt o nazwie `AddInCalcV1` do `CalculatorV1` rozwiązania. Oparte na **biblioteki klas** szablonu.  
  
2.  W **Eksploratora rozwiązań**, Dodaj odwołanie do zestawu System.AddIn.dll do projektu.  
  
3.  Dodaj odwołanie do `Calc1AddInView` projektu. Wybierz odwołanie do projektu, a następnie w **właściwości**ustaw **Kopiuj lokalnie** do **False**. W języku Visual Basic należy używać **odwołania** karcie **właściwości projektu** można ustawić **Kopiuj lokalnie** do **False** odwołania projektu.  
  
4.  Zmień nazwę klasy `AddInCalcV1`.  
  
5.  W pliku klasy należy dodać odwołanie do przestrzeni nazw <xref:System.AddIn> i segmentów widoku dodatku: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` w języku Visual Basic).  
  
6.  Zastosuj <xref:System.AddIn.AddInAttribute> atrybutu `AddInCalcV1` klasy, aby zidentyfikować klasy jako dodatek.  
  
7.  Wprowadź `AddInCalcV1` klasa implementuje interfejs, który reprezentuje Widok dodatku: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` w języku Visual Basic).  
  
8.  Implementowanie członkowie `ICalculator` , zwracając wyniki obliczeń odpowiednie.  
  
     Poniższy kod przedstawia ukończone dodatku programu.  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. Opcjonalnie można tworzyć rozwiązania programu Visual Studio.  
  
## <a name="deploying-the-pipeline"></a>Wdrażania potoku  
 Teraz można przystąpić do tworzenia i wdrażania segmentów w dodatku do potoku wymagane struktury katalogów.  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a>Aby wdrożyć segmenty potoku  
  
1.  Dla każdego projektu w rozwiązaniu, użyj **kompilacji** karcie **właściwości projektu** ( **skompilować** kartę w języku Visual Basic) można ustawić wartość **ścieżka wyjściowa**  ( **ścieżkę wyjściową kompilacji** w języku Visual Basic). Jeśli nazwany folderze aplikacji `MyApp`, na przykład projekty będzie umieszczenie w następujących folderów:  
  
    |Projekt|Ścieżka|  
    |-------------|----------|  
    |AddInCalcV1|MyApp\Pipeline\AddIns\CalcV1|  
    |Calc1AddInSideAdapter|MyApp\Pipeline\AddInSideAdapters|  
    |Calc1AddInView|MyApp\Pipeline\AddInViews|  
    |Calc1Contract|MyApp\Pipeline\Contracts|  
    |Calc1Host|MyApp|  
    |Calc1HostSideAdapter|MyApp\Pipeline\HostSideAdapters|  
    |Calc1HVA|MyApp|  
  
    > [!NOTE]
    >  Jeśli zdecydujesz się na umieszczenie Twoja struktura folderów potoku w lokalizacji innej niż folder aplikacji, należy zmodyfikować ścieżek przedstawionych w tabeli, odpowiednio. Zobacz Omówienie wymagań katalogu potoku w [wymagania dotyczące opracowywania potoku](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
2.  Twórz rozwiązania Visual Studio.  
  
3.  Sprawdź katalogów aplikacji i potoku, aby upewnić się, że zestawy zostały skopiowane do katalogu poprawny katalogów, a nie dodatkowe kopie zestawów zostały zainstalowane w folderach problem.  
  
    > [!NOTE]
    >  Jeśli nie zmieniono **Kopiuj lokalnie** do **False** dla `Calc1AddInView` projektu odwołania w `AddInCalcV1` projektu, problemy kontekst modułu ładującego uniemożliwi dodatek znajdujących się.  
  
     Aby uzyskać informacji o wdrażaniu do potoku, zobacz [wymagania dotyczące opracowywania potoku](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
## <a name="running-the-host-application"></a>Uruchamianie aplikacji hosta  
 Teraz można przystąpić do uruchamiania hosta i korzystać z dodatku.  
  
#### <a name="to-run-the-host-application"></a>Aby uruchomić aplikację hosta  
  
1.  W wierszu polecenia przejdź do katalogu aplikacji i uruchom aplikację hosta `Calc1Host.exe`.  
  
2.  Host znajduje wszystkie dostępne dodatki dla jego typu i monit o wybranie dodatku. Wprowadź **1** jedyną dostępną dodatku.  
  
3.  Wprowadź równania Kalkulator, taki jak **2 + 2**. Musi to być odstępy między liczb i operatora.  
  
4.  Typ **wyjść** i naciśnij klawisz **Enter** klawisz, aby zamknąć aplikację.  
  
## <a name="see-also"></a>Zobacz też  
- [Przewodnik: Włączanie zgodności z poprzednimi wersjami w miarę zmieniania hosta](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
-  [Wskazówki: Przekazywanie kolekcji między hostami i dodatkami](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
-  [Wymagania dotyczące opracowywania potoku](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
-  [Kontrakty, widoki i adaptery](https://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)  
-  [Opracowywanie potoku](../../../docs/framework/add-ins/pipeline-development.md)
