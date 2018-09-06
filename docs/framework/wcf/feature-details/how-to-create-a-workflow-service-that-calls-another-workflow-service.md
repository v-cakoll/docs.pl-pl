---
title: 'Instrukcje: Tworzenie usługi przepływu pracy wywołującej inną usługę przepływu pracy'
ms.date: 03/30/2017
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
ms.openlocfilehash: 1b30da34f7c85cccd98b18cd32b81c83630989b2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43725062"
---
# <a name="how-to-create-a-workflow-service-that-calls-another-workflow-service"></a>Instrukcje: Tworzenie usługi przepływu pracy wywołującej inną usługę przepływu pracy

Czasami konieczne jest uzyskanie informacji z inną usługę przepływu pracy usługi przepływu pracy. W tym temacie przedstawiono sposób wywoływania jednej usługi przepływu pracy z innego. W tym temacie utworzymy dwie usługi przepływu pracy; taki, który ma metodę cofającą ciągu wejściowego, a druga, która konwertuje ciąg wejściowy na wielkie litery, po wycofaniu ciąg, który korzysta z pierwszej usługi.

### <a name="to-create-the-reverser-workflow-service"></a>Tworzenie usługi przepływu pracy system

1.  Otwórz program Visual Studio.

2.  Wybierz **pliku** > **nowy projekt**. W obszarze **przepływu pracy** w węźle **zainstalowane szablony** okienku wybierz **aplikacja usługi przepływu pracy WCF**. Nazwij rozwiązanie `NestedServices` a następnie kliknij przycisk **OK**.

3.  W obszarze **serwerów**, upewnij się, że **użycia lokalnego serwera sieci Web usług IIS** jest zaznaczone. Kliknij przycisk **Utwórz katalog wirtualny**. Kliknij przycisk **OK** w oknie dialogowym stwierdzające katalog wirtualny został pomyślnie utworzony.

4.  W Eksploratorze rozwiązań, zmienianie nazwy Service1.xamlx do `StringReverserService.xamlx`.

5.  Na **właściwości projektu** strony dla nowego projektu, kliknij przycisk **Web** kartę. Ustaw **Akcja uruchamiania** do **konkretnej strony**i wybierz StringReverserService.xamlx jako stronę aby rozpocząć.

6.  Otwórz StringReverserService.xamlx w projektancie, a następnie usuń istniejącą `ReceiveRequest` i `SendReply` działań, a następnie przeciągnij `ReceiveAndSendReply` działanie do istniejącego działania sekwencji.

    1.  Ustaw **OperationName** do ReverseString.

    2.  Ustaw **ServiceContractName** do IReverseString.

    3.  Wybierz **CanCreateInstance** pole wyboru.

7.  Wybierz **SequentialService** działania, a następnie kliknij **zmienne** karty u dołu projektanta. Utwórz dwa nowe zmienne o nazwach StringToReverse i ReversedStringToReturn typu String.

8.  Kliknij przycisk **Definiuj** łącze w **Receive** działania. Kliknij przycisk **parametry**i utworzyć parametr o nazwie InputString typu ciąg, który przypisuje StringToReverse.

9. Kliknij przycisk **Definiuj** łącze w **SendReplyToReceive** działania. Kliknij przycisk **parametry**i utworzyć parametr o nazwie ReversedString typu String, przypisany do ReversedStringToReturn.

10. Aby zaimplementować logikę dla usługi, Utwórz nową klasę w projekcie o nazwie StringLibrary.  Zastąp definicję klasy z następującym kodem.

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

11. Aby wywołać metodę ReverseString w danych wejściowych, przeciągnij **InvokeMethod** działania z przybornika odstęp między **Receive** i **SendReply** działań. Ustaw właściwości działania w następujący sposób:

    1.  **MethodName**: ReverseString

    2.  **Wynik**: ReversedStringToReturn

    3.  **Parametry**: Tworzenie nowego parametru za pomocą **kierunek** z In, **typu** ciągu, a **wartość** z StringToReverse.

    4.  **TargetType**: NestedServices.StringLibrary

12. Testować usługę, naciskając klawisz F5. W kliencie testowym WCF, która jest wyświetlana kliknij dwukrotnie metodę ReverseString(). W okienku żądanie wprowadź `Sample` dla wartości parametru InputString. Kliknij przycisk **wywołania**. Usługa powinna zwrócić "elpmaS".

### <a name="to-create-the-uppercaser-workflow-service"></a>Tworzenie usługi przepływu pracy UpperCaser

1.  Kliknij prawym przyciskiem myszy projekt NestedServices, a następnie wybierz pozycję **Dodaj** > **nowy element**. W **przepływu pracy** węzeł **usługi przepływu pracy WCF**i nadaj nazwę nowej usługi `UpperCaserService`. Kliknij przycisk **Dodaj**. Powinno to dodanie nowej usługi przepływu pracy o nazwie UpperCaserService.xamlx do projektu.

2.  Otwórz UpperCaserService.xamlx w projektancie, a następnie usuń istniejącą **ReceiveRequest** i `SendReply` działań, a następnie przeciągnij `ReceiveAndSendReply` działanie do istniejącego działania sekwencji.

    1.  Ustaw **OperationName** do UpperCaseString.

    2.  Ustaw **ServiceContractName** do IUpperCaseString.

    3.  Wybierz **CanCreateInstance** pole wyboru.

3.  Wybierz działanie SequentialService, a następnie kliknij przycisk **zmienne** karty u dołu projektanta. Utwórz trzy nowe zmienne o nazwach StringToUpper, StringToReverse i StringToReturn typu String.

4.  Kliknij przycisk **Definiuj** łącze w **Receive** działania. Kliknij przycisk **parametry**i utworzyć parametr o nazwie InputString typu ciąg, który przypisuje StringToUpper.

5.  Kliknij przycisk **Definiuj** łącze w **SendReplyToReceive** działania. Kliknij przycisk **parametry**i utworzyć parametr o nazwie ModifiedString typu String, przypisany do StringToReturn.

6.  Aby zaimplementować logikę dla usługi, utworzenie nowej metody w klasie StringLibrary, używając następującego kodu.

    ```
    public static String UpperCaseString(string StringToUpperCase)
    {
         return StringToUpperCase.ToUpper();

    }
    ```

7.  Aby wywołać metodę UpperCaseString w danych wejściowych, przeciągnij **InvokeMethod** działania z przybornika odstęp między **Receive** i **SendReply** działań. Ustaw właściwości działania w następujący sposób:

    1.  **MethodName**: UpperCaseString

    2.  **Wynik**: StringToReverse

    3.  **Parametry**: Tworzenie nowego parametru za pomocą **kierunek** z In, **typu** ciągu, a **wartość** z StringToUpper.

    4.  **TargetType**: NestedServices.StringLibrary

8.  Teraz Zadzwonimy pierwszej usługi zmodyfikowaną wersją tego ciągu. Kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **odwołanie do usługi**. Dodaj odwołanie do niej usługi http://localhost/NestedServices/StringReverserService.xamlx i skompiluj projekt, aby utworzyć niestandardowe działanie, aby uzyskać dostęp do pierwszego usługi sieci Web.

9. Przeciągnij nowe działanie wystąpienia przepływu pracy, między **InvokeMethod** działania i **SendReplyToReceive** działań. Przypisywanie zmiennej StringToReverse właściwością InputString nowe działanie i zmiennych StringToReturn właściwości StringToReturn.

10. Otwórz stronę właściwości dla projektu NestedServices i zmień **konkretnej strony** w **Web** kartę, aby UpperCaserService.xamlx.

11. Testować usługę, naciskając klawisz F5. W kliencie testowym WCF, która jest wyświetlana kliknij dwukrotnie metodę ReverseString(). W okienku żądanie wprowadź `Sample` dla wartości parametru InputString. Kliknij przycisk **wywołania**. Usługa powinna zwrócić "ELPMAS".

### <a name="to-create-a-client-to-call-the-services"></a>Można utworzyć klienta do wywołania usługi

1.  Dodaj nowy projekt aplikacji konsoli, nazywane klienta do rozwiązania.

2.  Kliknij prawym przyciskiem myszy projekt klienta, a następnie wybierz pozycję **Dodaj** > **odwołanie do usługi**. W wyświetlonym oknie kliknij **odnajdź**. Wybierz StringReverserService.xamlx i wprowadzili ReverseService przestrzeni nazw.  Kliknij przycisk **OK**.

3.  Zastąp metodę Main w pliku Program.cs następującym kodem.

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