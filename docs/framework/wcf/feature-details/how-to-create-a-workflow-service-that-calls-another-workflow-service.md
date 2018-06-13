---
title: 'Instrukcje: Tworzenie usługi przepływu pracy wywołującej inną usługę przepływu pracy'
ms.date: 03/30/2017
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
ms.openlocfilehash: fda5a7286c3d20c7cdc2093e58bfe3fbdcf1d1c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497194"
---
# <a name="how-to-create-a-workflow-service-that-calls-another-workflow-service"></a>Instrukcje: Tworzenie usługi przepływu pracy wywołującej inną usługę przepływu pracy
Czasami jest niezbędne dla usługi przepływu pracy można uzyskać informacji z innej usługi przepływu pracy.  W tym temacie przedstawiono sposób wywoływania jednej usługi przepływu pracy z innej. W tym temacie utworzymy dwie usługi przepływu pracy; jeden, który ma metodę, która odwraca ciągu wejściowego, a druga konwertujący ciągu wejściowego na wielkie litery, po wycofaniu ciąg, który używa pierwszej usługi.  
  
### <a name="to-create-the-reverser-workflow-service"></a>Aby utworzyć system usługi przepływu pracy  
  
1.  Uruchom [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] jako administrator.  
  
2.  Wybierz **pliku**, **nowy projekt**. W obszarze **przepływu pracy** w węźle **zainstalowane szablony** okienku wybierz **aplikacji usługi przepływu pracy WCF**. Nazwa rozwiązania `NestedServices` , a następnie kliknij przycisk **OK**.  
  
3.  W obszarze **serwerów**, upewnij się, że **użycia lokalnego serwera sieci Web usług IIS** jest zaznaczone. Kliknij przycisk **utworzyć katalog wirtualny**. Kliknij przycisk **OK** w okno dialogowe podając pomyślnie utworzono katalog wirtualny.  
  
4.  W Eksploratorze rozwiązań, Zmień nazwę Service1.xamlx do `StringReverserService.xamlx`.  
  
5.  Na **właściwości projektu** dla nowego projektu kliknij pozycję **Web** kartę. Ustaw **Akcja uruchamiania** do **określonej strony**i wybierz StringReverserService.xamlx jako strony, aby rozpocząć.  
  
6.  Otwórz w Projektancie StringReverserService.xamlx i usuń istniejącą `ReceiveRequest` i `SendReply` działania, a następnie przeciągnij `ReceiveAndSendReply` działania do istniejącego działania sekwencji.  
  
    1.  Ustaw **OperationName** do ReverseString.  
  
    2.  Ustaw **ServiceContractName** do IReverseString.  
  
    3.  Wybierz **CanCreateInstance** pole wyboru.  
  
7.  Wybierz **SequentialService** działania, a następnie kliknij przycisk **zmienne** u dołu projektanta. Utwórz dwa nowe zmienne o nazwach StringToReverse i ReversedStringToReturn typu String.  
  
8.  Kliknij przycisk **Definiuj** łącze w **Receive** działania. Kliknij przycisk **parametry**i Utwórz parametr o nazwie InputString typu ciąg, który przypisuje StringToReverse.  
  
9. Kliknij przycisk **Definiuj** łącze w **SendReplyToReceive** działania. Kliknij przycisk **parametry**i Utwórz parametr o nazwie ReversedString typu ciąg, przypisane do ReversedStringToReturn.  
  
10. Aby zaimplementować logiki dla usługi, Utwórz nową klasę w projekcie o nazwie StringLibrary.  Zastąp definicję klasy następującym kodem.  
  
    ```  
    public class StringLibrary  
        {  
            public static String ReverseString(string StringToReverse)  
            {  
                char[] charArray = StringToReverse.ToCharArray();  
                Array.Reverse(charArray);  
                return new String(charArray);  
            }  
        }  
    ```  
  
11. Aby wywołać metodę ReverseString w danych wejściowych, przeciągnij **InvokeMethod** działania z przybornika do odstęp między **Receive** i **SendReply** działań. Ustaw właściwości działania w następujący sposób:  
  
    1.  **MethodName**: ReverseString  
  
    2.  **Wynik**: ReversedStringToReturn  
  
    3.  **Parametry**: Utwórz nowy parametr z **kierunek** z In, **typu** ciągu, a **wartość** z StringToReverse.  
  
    4.  **Element TargetType**: NestedServices.StringLibrary  
  
12. Przetestuj usługę, naciskając klawisz F5. W kliencie testowym WCF, która jest wyświetlana kliknij dwukrotnie metodę ReverseString(). W okienku żądania wprowadź `Sample` dla wartości parametru InputString. Kliknij przycisk **wywołania**. Usługa powinna zwrócić "elpmaS".  
  
### <a name="to-create-the-uppercaser-workflow-service"></a>Aby utworzyć UpperCaser usługi przepływu pracy  
  
1.  Kliknij prawym przyciskiem myszy projekt NestedServices i wybierz **Dodaj**, **nowy element**. W **przepływu pracy** węzła, wybierz opcję **usługi przepływu pracy WCF**i nadaj nazwę nowej usługi `UpperCaserService`. Kliknij przycisk **Dodaj**. To należy dodać nową usługę przepływu pracy o nazwie UpperCaserService.xamlx do projektu.  
  
2.  Otwórz w Projektancie UpperCaserService.xamlx i usuń istniejącą **ReceiveRequest** i `SendReply` działania i przeciągnij `ReceiveAndSendReply` działania do istniejącego działania sekwencji.  
  
    1.  Ustaw **OperationName** do UpperCaseString.  
  
    2.  Ustaw **ServiceContractName** do IUpperCaseString.  
  
    3.  Wybierz **CanCreateInstance** pole wyboru.  
  
3.  Wybierz działanie SequentialService, a następnie kliknij przycisk **zmienne** u dołu projektanta. Utwórz trzy nowe zmienne o nazwach StringToUpper, StringToReverse i StringToReturn typu String.  
  
4.  Kliknij przycisk **Definiuj** łącze w **Receive** działania. Kliknij przycisk **parametry**i Utwórz parametr o nazwie InputString typu ciąg, który przypisuje StringToUpper.  
  
5.  Kliknij przycisk **Definiuj** łącze w **SendReplyToReceive** działania. Kliknij przycisk **parametry**i Utwórz parametr o nazwie ModifiedString typu ciąg, przypisane do StringToReturn.  
  
6.  Aby zaimplementować logiki dla usługi, utworzenie nowej metody w klasie StringLibrary, używając następującego kodu.  
  
    ```  
    public static String UpperCaseString(string StringToUpperCase)  
    {  
         return StringToUpperCase.ToUpper();  
  
    }  
    ```  
  
7.  Aby wywołać metodę UpperCaseString w danych wejściowych, przeciągnij **InvokeMethod** działania z przybornika do odstęp między **Receive** i **SendReply** działań. Ustaw właściwości działania w następujący sposób:  
  
    1.  **MethodName**: UpperCaseString  
  
    2.  **Wynik**: StringToReverse  
  
    3.  **Parametry**: Utwórz nowy parametr z **kierunek** z In, **typu** ciągu, a **wartość** z StringToUpper.  
  
    4.  **Element TargetType**: NestedServices.StringLibrary  
  
8.  Teraz Zadzwonimy pierwszej usługi zmodyfikowany ciąg. Kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj odwołanie do usługi**. Dodawanie odwołania do usługi z usługą w http://localhost/NestedServices/StringReverserService.xamlx i skompiluj projekt do tworzenia działań niestandardowych do uzyskania dostępu do pierwszej usługi sieci Web.  
  
9. Przeciągnij wystąpienie nowego działania przepływu pracy, między **InvokeMethod** działania i **SendReplyToReceive** działań. Przypisz zmiennej StringToReverse z właściwością InputString nowe działanie i zmiennej StringToReturn właściwości StringToReturn.  
  
10. Otwórz stronę właściwości dla projektu NestedServices i zmień **określonej strony** w **Web** kartę, aby UpperCaserService.xamlx.  
  
11. Przetestuj usługę, naciskając klawisz F5. W kliencie testowym WCF, która jest wyświetlana kliknij dwukrotnie metodę ReverseString(). W okienku żądania wprowadź `Sample` dla wartości parametru InputString. Kliknij przycisk **wywołania**. Usługa powinna zwrócić "ELPMAS".  
  
### <a name="to-create-a-client-to-call-the-services"></a>Aby utworzyć klienta do wywołania usługi  
  
1.  Dodaj nowy projekt aplikacji konsoli o nazwie klienta do rozwiązania.  
  
2.  Kliknij prawym przyciskiem myszy projekt klienta i wybierz **Dodaj odwołanie do usługi**. W wyświetlonym oknie kliknij **odnajdowania**. Wybierz StringReverserService.xamlx, a następnie wprowadź ReverseService jako obszar nazw.  Kliknij przycisk **OK**.  
  
3.  Zastąp metodę Main, w pliku Program.cs następującym kodem.  
  
    ```  
    static void Main(string[] args)  
    {  
        Console.Write("Input string to process:");  
        String input = Console.ReadLine();  
        var service = new ReverseService.ReverseStringClient();  
        Console.WriteLine("Output from service: {0}", service.ReverseString(input));  
        Console.ReadKey();  
    }  
    ```
