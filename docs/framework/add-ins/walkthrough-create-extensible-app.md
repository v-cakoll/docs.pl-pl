---
title: "Wskazówki: tworzenie aplikacji rozszerzalnej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "32"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6609f30844421f94965fbe05114db96ed8edbb31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-an-extensible-application"></a>Wskazówki: tworzenie aplikacji rozszerzalnej
Ten przewodnik zawiera opis sposobu tworzenia potoku dodatku pełni prosty kalkulator funkcji. Nie wykazują rzeczywistych scenariuszy; zamiast go przedstawiono podstawowe funkcje potoku i jak dodatek może zapewnić usługi hosta.  
  
 W tym przewodniku opisano następujące zadania:  
  
-   Tworzenie rozwiązania Visual Studio.  
  
-   Tworzenie potoku struktury katalogów.  
  
-   Trwa tworzenie kontraktu i widoków.  
  
-   Tworzenie Dodaj strony karty.  
  
-   Tworzenie karty po stronie hosta.  
  
-   Tworzenie hosta.  
  
-   Tworzenie dodatku.  
  
-   Wdrażanie potoku.  
  
-   Uruchomienie aplikacji hosta.  
  
 Tego potoku przekazuje tylko dla typów możliwych do serializacji (<xref:System.Double> i <xref:System.String>), między hostem a dodatku. Na przykład pokazujący sposób przekazywania kolekcji typów złożonych danych zobacz [wskazówki: przekazywanie kolekcje między hostami i dodatki](http://msdn.microsoft.com/en-us/b532c604-548e-4fab-b11c-377257dd0ee5).  
  
 Model obiektowy cztery operacje arytmetyczne definiuje kontrakt dla tego potoku: Dodawanie, odejmowanie mnożenia i dzielenia. Host udostępnia dodatek równości, aby obliczyć, takich jak 2 + 2 i dodatek zwraca wynik do hosta.  
  
 W wersji 2 dodatku Kalkulator zapewnia możliwości bardziej obliczania i prezentuje przechowywania wersji. Opisano w [wskazówki: Włączanie zgodności z poprzednimi wersjami jako Twoje zmiany hosta](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebne w tym przewodniku:  
  
-   [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="creating-a-visual-studio-solution"></a>Tworzenie rozwiązania Visual Studio  
 Za pomocą rozwiązania w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zawiera projekty segmentów potoku.  
  
#### <a name="to-create-the-pipeline-solution"></a>Tworzenie rozwiązań potoku  
  
1.  W [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], Utwórz nowy projekt o nazwie `Calc1Contract`. Na podstawie **biblioteki klas** szablonu.  
  
2.  Nazwa rozwiązania `CalculatorV1`.  
  
## <a name="creating-the-pipeline-directory-structure"></a>Tworzenie potoku struktury katalogów  
 Model dodatku wymaga zestawy segmentów potoku do umieszczenia w strukturze określonego katalogu. Aby uzyskać więcej informacji o strukturze potoku, zobacz [wymagania rozwój potoku](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
#### <a name="to-create-the-pipeline-directory-structure"></a>Aby utworzyć struktury katalogu potoku  
  
1.  Utwórz folder aplikacji dowolnego miejsca na tym komputerze.  
  
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
  
     Nie jest konieczne umieszczanie potoku struktury folderów w folderze aplikacji; została ona wysłana tutaj wyłącznie dla wygody. Na odpowiedni krok przewodnika wyjaśniono, jak zmienić kod, jeśli struktura folderów potoku jest w innej lokalizacji. Zawiera omówienie wymagań katalogu potoku w [wymagania rozwój potoku](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
    > [!NOTE]
    >  `CalcV2` Folder nie jest używany w tym przewodniku; jest symbolem zastępczym dla [wskazówki: Włączanie zgodności z poprzednimi wersjami jako Twoje zmiany hosta](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848).  
  
## <a name="creating-the-contract-and-views"></a>Tworzenie kontraktu i widoków  
 Definiuje kontrakt segmentu dla tego potoku `ICalc1Contract` interfejs, który definiuje cztery metody: `add`, `subtract`, `multiply`, i `divide`.  
  
#### <a name="to-create-the-contract"></a>Aby utworzyć kontrakt  
  
1.  W rozwiązaniu Visual Studio o nazwie `CalculatorV1`, otwórz `Calc1Contract` projektu.  
  
2.  W **Eksploratora rozwiązań**, dodaj odwołania do następujących zestawów do `Calc1Contract` projektu:  
  
     System.AddIn.Contract.dll  
  
     System.AddIn.dll  
  
3.  W **Eksploratora rozwiązań**, Wyklucz domyślną klasę, który jest dodawany do nowego **biblioteki klas** projektów.  
  
4.  W **Eksploratora rozwiązań**, Dodaj nowy element do projektu przy użyciu **interfejsu** szablonu. W **Dodaj nowy element** okno dialogowe, nazwa interfejsu `ICalc1Contract`.  
  
5.  W pliku interfejsu dodać odwołania do przestrzeni nazw do <xref:System.AddIn.Contract> i <xref:System.AddIn.Pipeline>.  
  
6.  Użyć poniższego kodu, aby ukończyć ten segment kontraktu. Należy pamiętać, że ten interfejs musi mieć <xref:System.AddIn.Pipeline.AddInContractAttribute> atrybutu.  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  Opcjonalnie tworzenie rozwiązań programu Visual Studio. Nie można uruchomić do momentu ostatnia procedura, ale skompilowanie go po każdej procedury powoduje, że każdy projekt ma Popraw.  
  
 Ponieważ widok dodatku i host Widok dodatku zwykle mają ten sam kod, szczególnie w pierwszej wersji dodatku, można jednak łatwo tworzyć widoki w tym samym czasie. Różnią się tylko jeden składnik: Wyświetl dodatek wymaga <xref:System.AddIn.Pipeline.AddInBaseAttribute> atrybutu, podczas gdy widoku hosta dodatku nie wymagają żadnych atrybutów.  
  
#### <a name="to-create-the-add-in-view"></a>Aby utworzyć widok dodatku  
  
1.  Dodawanie nowego projektu o nazwie `Calc1AddInView` do `CalculatorV1` rozwiązania. Na podstawie **biblioteki klas** szablonu.  
  
2.  W **Eksploratora rozwiązań**, Dodaj odwołanie do System.AddIn.dll do `Calc1AddInView` projektu.  
  
3.  W **Eksploratora rozwiązań**, Wyklucz domyślną klasę, który jest dodawany do nowego **biblioteki klas** projektów, a następnie dodaj nowy element do projektu przy użyciu **interfejsu** szablonu. W **Dodaj nowy element** okno dialogowe, nazwa interfejsu `ICalculator`.  
  
4.  W pliku interfejs Dodaj odwołanie do przestrzeni nazw <xref:System.AddIn.Pipeline>.  
  
5.  Aby ukończyć ten widok dodatku, należy użyć poniższego kodu. Należy pamiętać, że ten interfejs musi mieć <xref:System.AddIn.Pipeline.AddInBaseAttribute> atrybutu.  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  Opcjonalnie tworzenie rozwiązań programu Visual Studio.  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a>Aby utworzyć widok hosta dodatku  
  
1.  Dodawanie nowego projektu o nazwie `Calc1HVA` do `CalculatorV1` rozwiązania. Na podstawie **biblioteki klas** szablonu.  
  
2.  W **Eksploratora rozwiązań**, Wyklucz domyślną klasę, który jest dodawany do nowego **biblioteki klas** projektów, a następnie dodaj nowy element do projektu przy użyciu **interfejsu** szablonu. W **Dodaj nowy element** okno dialogowe, nazwa interfejsu `ICalculator`.  
  
3.  W pliku interfejsu należy użyć poniższego kodu do wykonania widoku hosta dodatku.  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  Opcjonalnie tworzenie rozwiązań programu Visual Studio.  
  
## <a name="creating-the-add-in-side-adapter"></a>Tworzenie karty Dodaj strony  
 Ta karta dodać stronie składa się z jednej karty widoku do kontraktu. Ten segment potoku konwertuje typy w widoku Dodaj umowy.  
  
 W tym potoku dodatku udostępnia usługę na hoście, a typy przepływać z dodatku do hosta. Ponieważ żaden z typów przepływać z hosta do dodatku, masz nie zawiera karty Widok kontraktów po stronie dodatku tego potoku.  
  
#### <a name="to-create-the-add-in-side-adapter"></a>Aby utworzyć karty Dodaj strony  
  
1.  Dodawanie nowego projektu o nazwie `Calc1AddInSideAdapter` do `CalculatorV1` rozwiązania. Na podstawie **biblioteki klas** szablonu.  
  
2.  W **Eksploratora rozwiązań**, dodaj odwołania do następujących zestawów do `Calc1AddInSideAdapter` projektu:  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  Dodawanie odwołań do projektów dla segmentów potoku sąsiadujących projektu:  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  Wybierz odwołanie do każdego projektu, a następnie w **właściwości** ustawić **Kopiuj lokalnie** do **False**. W języku Visual Basic, użyj **odwołania** karty **właściwości projektu** można ustawić **Kopiuj lokalnie** do **False** projektu dwa odwołania.  
  
5.  Zmień nazwę projektu domyślną klasę `CalculatorViewToContractAddInSideAdapter`.  
  
6.  Plik klasy, dodaj odwołania do przestrzeni nazw do <xref:System.AddIn.Pipeline>.  
  
7.  Plik klasy, dodaj odwołania do przestrzeni nazw dla sąsiadujących segmentów: `CalcAddInViews` i `CalculatorContracts`. (W języku Visual Basic są te odwołania do przestrzeni nazw `Calc1AddInView.CalcAddInViews` i `Calc1Contract.CalculatorContracts`, chyba że wyłączono domyślne obszary nazw w projektach Visual Basic.)  
  
8.  Zastosuj <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atrybutu `CalculatorViewToContractAddInSideAdapter` klasy, aby zidentyfikować go jako Dodaj strony karty.  
  
9. Należy `CalculatorViewToContractAddInSideAdapter` klasa dziedziczy <xref:System.AddIn.Pipeline.ContractBase>, który udostępnia domyślną implementację <xref:System.AddIn.Contract.IContract> interfejsu i implementować interfejs kontraktu dla potoku, `ICalc1Contract`.  
  
10. Dodaj publiczny konstruktor, który akceptuje `ICalculator`, przechowuje go w pole prywatne i wywołuje konstruktor klasy podstawowej.  
  
11. Aby zaimplementować członków `ICalc1Contract`, po prostu Wywołaj odpowiednie elementy członkowskie z `ICalculator` wystąpienia, który jest przekazywany do konstruktora, a następnie zwracają wyniki. To dostosowuje widok (`ICalculator`) do kontraktu (`ICalc1Contract`).  
  
     Poniższy kod przedstawia ukończone karty Dodaj strony.  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. Opcjonalnie tworzenie rozwiązań programu Visual Studio.  
  
## <a name="creating-the-host-side-adapter"></a>Tworzenie karty po stronie hosta  
 Ta karta po stronie hosta składa się z jednej karty kontraktu do widoku. Ten segment dostosowuje kontraktu do widoku hosta dodatku.  
  
 W tym potoku dodatku udostępnia usługę do hosta i przepływ typów z dodatku do hosta. Ponieważ żaden z typów przepływać z hosta do dodatku, masz nie zawiera karty widoku do kontraktu.  
  
 Aby zaimplementować Zarządzanie okresem istnienia, należy użyć <xref:System.AddIn.Pipeline.ContractHandle> obiekt można dołączyć do kontraktu tokenu okresu istnienia. Odwołanie do tego dojścia muszą zapewnić, aby zarządzanie okresem istnienia do pracy. Po zastosowaniu token nie dodatkowego programowania jest wymagana, ponieważ system dodatku można zlikwidować obiektów gdy nie są używane i udostępnienia ich do pamięci. Aby uzyskać więcej informacji, zobacz [Zarządzanie okresem istnienia](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).  
  
#### <a name="to-create-the-host-side-adapter"></a>Aby utworzyć karty po stronie hosta  
  
1.  Dodawanie nowego projektu o nazwie `Calc1HostSideAdapter` do `CalculatorV1` rozwiązania. Na podstawie **biblioteki klas** szablonu.  
  
2.  W **Eksploratora rozwiązań**, dodaj odwołania do następujących zestawów do `Calc1HostSideAdapter` projektu:  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  Dodawanie odwołań do projektów dla sąsiadujących segmentów projektu:  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  Wybierz odwołanie do każdego projektu, a następnie w **właściwości** ustawić **Kopiuj lokalnie** do **False**. W języku Visual Basic, użyj **odwołania** karty **właściwości projektu** można ustawić **Kopiuj lokalnie** do **False** projektu dwa odwołania.  
  
5.  Zmień nazwę projektu domyślną klasę `CalculatorContractToViewHostSideAdapter`.  
  
6.  Plik klasy, dodaj odwołania do przestrzeni nazw do <xref:System.AddIn.Pipeline>.  
  
7.  Plik klasy, dodaj odwołania do przestrzeni nazw dla sąsiadujących segmentów: `CalcHVAs` i `CalculatorContracts`. (W języku Visual Basic są te odwołania do przestrzeni nazw `Calc1HVA.CalcHVAs` i `Calc1Contract.CalculatorContracts`, chyba że wyłączono domyślne obszary nazw w projektach Visual Basic.)  
  
8.  Zastosuj <xref:System.AddIn.Pipeline.HostAdapterAttribute> atrybutu `CalculatorContractToViewHostSideAdapter` klasy, aby zidentyfikować go jako segment karty po stronie hosta.  
  
9. Wprowadź `CalculatorContractToViewHostSideAdapter` klasa implementuje interfejs, który reprezentuje widoku hosta dodatku: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` w języku Visual Basic).  
  
10. Dodaj publicznego konstruktora akceptującego typ kontraktu potoku `ICalc1Contract`. Konstruktor musi pamięci podręcznej odwołanie do kontraktu. Należy także utworzyć i pamięci podręcznej nowy <xref:System.AddIn.Pipeline.ContractHandle> kontraktu, do zarządzania przez czas ich istnienia dodatku.  
  
    > [!IMPORTANT]
    >  <xref:System.AddIn.Pipeline.ContractHandle> Jest najważniejszym czynnikiem umożliwiającym zarządzanie okresem istnienia. Jeśli nie zostanie utrzymywać odwołania do <xref:System.AddIn.Pipeline.ContractHandle> obiektu, wyrzucanie elementów bezużytecznych spowoduje jego odzyskanie i potoku zostanie zamknięty, gdy program nie oczekuje. Może to prowadzić do błędów, które są trudne do diagnozowania, takich jak <xref:System.AppDomainUnloadedException>. Zamknięcie jest normalne etap życia potoku, nie istnieje sposób zarządzania okres istnienia kodu wykrywa, że ten stan jest błąd.  
  
11. Aby zaimplementować członków `ICalculator`, po prostu Wywołaj odpowiednie elementy członkowskie z `ICalc1Contract` wystąpienia, który jest przekazywany do konstruktora, a następnie zwracają wyniki. Dostosowuje to kontrakt (`ICalc1Contract`) do widoku (`ICalculator`).  
  
     Poniższy kod przedstawia ukończone karty po stronie hosta.  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. Opcjonalnie tworzenie rozwiązań programu Visual Studio.  
  
## <a name="creating-the-host"></a>Tworzenie hosta  
 Aplikacja hosta wchodzi w interakcję z dodatku za pośrednictwem widoku hosta dodatku. Używa dodatku odnajdywania aktywacji metody i udostępniane przez <xref:System.AddIn.Hosting.AddInStore> i <xref:System.AddIn.Hosting.AddInToken> klasy wykonać następujące czynności:  
  
-   Aktualizacja pamięci podręcznej informacji o potoku i dodatku.  
  
-   Znajdź dodatki typu widoku hosta `ICalculator`, w katalogu głównym określonej potoku.  
  
-   Monituj użytkownika do określenia, które dodatku do użycia.  
  
-   Aktywuj wybrany dodatek w nowej domenie z poziomem zaufania zabezpieczeń określonych aplikacji.  
  
-   Uruchom niestandardowego `RunCalculator` metodę, która wywołuje metody dodatku dla określonych w widoku hosta dodatku.  
  
#### <a name="to-create-the-host"></a>Aby utworzyć hosta  
  
1.  Dodawanie nowego projektu o nazwie `Calc1Host` do `CalculatorV1` rozwiązania. Na podstawie **aplikacji konsoli** szablonu.  
  
2.  W **Eksploratora rozwiązań**, Dodaj odwołanie do zestawu System.AddIn.dll do `Calc1Host` projektu.  
  
3.  Dodaj odwołanie projektu do `Calc1HVA` projektu. Wybierz odwołanie do projektu i **właściwości** ustawić **Kopiuj lokalnie** do **False**. W języku Visual Basic, użyj **odwołania** karcie **właściwości projektu** można ustawić **Kopiuj lokalnie** do **False**.  
  
4.  Zmień nazwę pliku klasy (moduł w języku Visual Basic) `MathHost1`.  
  
5.  W języku Visual Basic, użyj **aplikacji** karcie **właściwości projektu** okno dialogowe, aby ustawić **obiekt uruchomieniowy** do **Sub Main**.  
  
6.  W pliku klasę lub moduł, Dodaj odwołanie do przestrzeni nazw <xref:System.AddIn.Hosting>.  
  
7.  W pliku klasę lub moduł, dodaj odwołania do przestrzeni nazw dla widoku hosta dodatku: `CalcHVAs`. (W języku Visual Basic tego odwołania do przestrzeni nazw jest `Calc1HVA.CalcHVAs`, chyba że wyłączono domyślne obszary nazw w projektach Visual Basic.)  
  
8.  W **Eksploratora rozwiązań**, wybierz rozwiązanie i z **projektu** menu wybierz **właściwości**. W **strony właściwości rozwiązania** okno dialogowe, zestaw **jednego projektu startowego** za ten projekt aplikacji hosta.  
  
9. W pliku klasę lub moduł, użyj <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> metodę aktualizowania pamięci podręcznej. Użyj <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> metodę, aby uzyskać kolekcję tokenów oraz <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> metodę, aby aktywować dodatku.  
  
     Poniższy kod przedstawia aplikacji hosta ukończone.  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  Ten kod przyjęto założenie, że struktura folderów potoku znajduje się w folderze aplikacji. Jeśli użytkownik znajduje się on w innym miejscu, zmień wiersz kodu, który ustawia `addInRoot` zmiennej, tak aby zmienna zawiera ścieżkę do potoku struktury katalogów.  
  
     W kodzie użyto `ChooseCalculator` metodę do listy tokenów i monitowanie użytkownika o wybranie dodatku. `RunCalculator` Metoda monituje użytkownika o matematyczne proste wyrażenia, analizuje wyrażenia przy użyciu `Parser` klasy i wyświetla wyniki zwrócone przez dodatek.  
  
10. Opcjonalnie tworzenie rozwiązań programu Visual Studio.  
  
## <a name="creating-the-add-in"></a>Tworzenie dodatku  
 Dodatek implementuje metody określone przez widok dodatku. Ten dodatek implementuje `Add`, `Subtract`, `Multiply`, i `Divide` operacji oraz zwraca wyniki do hosta.  
  
#### <a name="to-create-the-add-in"></a>Aby utworzyć dodatku  
  
1.  Dodawanie nowego projektu o nazwie `AddInCalcV1` do `CalculatorV1` rozwiązania. Na podstawie **biblioteki klas** szablonu.  
  
2.  W **Eksploratora rozwiązań**, Dodaj odwołanie do zestawu System.AddIn.dll do projektu.  
  
3.  Dodaj odwołanie projektu do `Calc1AddInView` projektu. Wybierz odwołanie do projektu i **właściwości**ustaw **Kopiuj lokalnie** do **False**. W języku Visual Basic, użyj **odwołania** karcie **właściwości projektu** można ustawić **Kopiuj lokalnie** do **False** dla odwołania do projektu.  
  
4.  Zmień nazwę klasy `AddInCalcV1`.  
  
5.  Plik klasy, Dodaj odwołanie do przestrzeni nazw <xref:System.AddIn> i segmentów widoku dodatku: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` w języku Visual Basic).  
  
6.  Zastosuj <xref:System.AddIn.AddInAttribute> atrybutu `AddInCalcV1` klasy, aby zidentyfikować klasy jako dodatek.  
  
7.  Wprowadź `AddInCalcV1` klasa implementuje interfejs, który reprezentuje Widok dodatku: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` w języku Visual Basic).  
  
8.  Implementować członków `ICalculator` przez zwrócenie wyników obliczeń odpowiednie.  
  
     Poniższy kod przedstawia ukończone dodatek.  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. Opcjonalnie tworzenie rozwiązań programu Visual Studio.  
  
## <a name="deploying-the-pipeline"></a>Wdrażanie potoku  
 Teraz można przystąpić do tworzenia i wdrażania segmentów dodatku do potoku wymagane struktury katalogów.  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a>Aby wdrożyć segmentów potoku  
  
1.  Dla każdego projektu w rozwiązaniu, użyj **kompilacji** karcie **właściwości projektu** ( **skompilować** kartę w języku Visual Basic) można ustawić wartości **ścieżki wyjściowej**  ( **ścieżki wyjściowej kompilacji** w języku Visual Basic). Jeśli nazwany folderze aplikacji `MyApp`, na przykład projektów czy kompilacji do następujących folderów:  
  
    |Project|Ścieżka|  
    |-------------|----------|  
    |AddInCalcV1|MyApp\Pipeline\AddIns\CalcV1|  
    |Calc1AddInSideAdapter|MyApp\Pipeline\AddInSideAdapters|  
    |Calc1AddInView|MyApp\Pipeline\AddInViews|  
    |Calc1Contract|MyApp\Pipeline\Contracts|  
    |Calc1Host|Moja_aplikacja|  
    |Calc1HostSideAdapter|MyApp\Pipeline\HostSideAdapters|  
    |Calc1HVA|Moja_aplikacja|  
  
    > [!NOTE]
    >  Jeśli zdecydujesz się na umieszczanie strukturę folderu potoku w lokalizacji innej niż folderze aplikacji, należy zmodyfikować ścieżki odpowiednio wymienionych w tabeli. Zawiera omówienie wymagań katalogu potoku w [wymagania rozwój potoku](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
2.  Skompiluj rozwiązanie Visual Studio.  
  
3.  Sprawdź katalogów aplikacji i potoku, aby upewnić się, że zestawy zostały skopiowane do katalogów poprawne i czy w folderach niewłaściwy zostały zainstalowane żadne dodatkowe kopie zestawów.  
  
    > [!NOTE]
    >  Jeśli nie została zmieniona **Kopiuj lokalnie** do **False** dla `Calc1AddInView` projektu odwołania w `AddInCalcV1` projektu, problemów z kontekstami modułu ładującego uniemożliwi dodatek znajdujących się.  
  
     Informacje o wdrażaniu do potoku, zobacz [wymagania rozwój potoku](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
## <a name="running-the-host-application"></a>Uruchomienie aplikacji hosta  
 Teraz można przystąpić do uruchomienia hosta i interakcji z dodatku.  
  
#### <a name="to-run-the-host-application"></a>Aby uruchomić aplikację hosta  
  
1.  W wierszu polecenia przejdź do katalogu aplikacji i uruchomić aplikację hosta `Calc1Host.exe`.  
  
2.  Host znajduje wszystkie dostępne dodatki jej typu i wyświetla monit o wybranie dodatku. Wprowadź **1** dostępne tylko w dodatku.  
  
3.  Wprowadź równania Kalkulator, takich jak **2 + 2**. Musi to być odstępy między liczb i operatora.  
  
4.  Typ **zakończyć** i naciśnij klawisz **Enter** klawisz, aby zamknąć aplikację.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Włączanie zgodności z poprzednimi wersjami zmiana hosta](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [Wskazówki: Przekazywanie kolekcje między hostami oraz dodatki](http://msdn.microsoft.com/en-us/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [Wymagania dotyczące rozwój potoku](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [Kontrakty, widoków i kart](http://msdn.microsoft.com/en-us/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [Rozwój potoku](../../../docs/framework/add-ins/pipeline-development.md)
