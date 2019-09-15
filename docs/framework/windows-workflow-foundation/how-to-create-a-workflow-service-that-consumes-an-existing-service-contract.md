---
title: 'Instrukcje: Tworzenie usługi przepływu pracy wykorzystującej istniejący kontrakt usługi'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 6d7fa8c9faa84efc84243387cd27aa264f6155eb
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989624"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>Instrukcje: Tworzenie usługi przepływu pracy wykorzystującej istniejący kontrakt usługi
.NET Framework 4,5 funkcje lepsza integracja między usługami sieci Web i przepływami pracy w formie tworzenia przepływu pracy w pierwszej kolejności. Narzędzie do tworzenia przepływu pracy pierwszego kontraktu umożliwia zaprojektowanie kontraktu w kodzie. Narzędzie automatycznie generuje szablon działania w przyborniku dla operacji w kontrakcie.  
  
> [!NOTE]
> Ten temat zawiera wskazówki krok po kroku dotyczące tworzenia usługi przepływu pracy pierwszego kontraktu. Aby uzyskać więcej informacji na temat tworzenia usługi przepływu pracy w pierwszej kolejności, zobacz [pierwsze programowanie usługi przepływu pracy w ramach kontraktu](contract-first-workflow-service-development.md).  
  
### <a name="creating-the-workflow-project"></a>Tworzenie projektu przepływu pracy  
  
1. W programie Visual Studio wybierz pozycję **plik**, **Nowy projekt**. Wybierz węzeł **WCF** w **C#** węźle drzewa **szablonów** , a następnie wybierz szablon **aplikacja usługi przepływu pracy WCF** .  
  
2. Nazwij nowy projekt `ContractFirst` , a następnie kliknij przycisk **OK**.  
  
### <a name="creating-the-service-contract"></a>Tworzenie kontraktu usługi  
  
1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**, **nowy element.** ... Wybierz węzeł **kod** po lewej stronie i szablon **klasy** po prawej stronie. Nazwij nową klasę `IBookService` i kliknij przycisk **OK**.  
  
2. W górnej części wyświetlonego okna kod Dodaj instrukcję using do `System.Servicemodel`.  
  
    ```csharp  
    using System.ServiceModel;  
    ```  
  
3. Zmień definicję klasy przykładowej na następującą definicję interfejsu.  
  
    ```csharp  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. Skompiluj projekt, naciskając **klawisze CTRL + SHIFT + B**.  
  
### <a name="importing-the-service-contract"></a>Importowanie kontraktu usługi  
  
1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** a następnie wybierz pozycję **Importuj kontrakt usługi**. W obszarze  **\<bieżący projekt >** Otwórz wszystkie węzły podrzędne i wybierz pozycję **IBookService**. Kliknij przycisk **OK**.  
  
2. Zostanie otwarte okno dialogowe z alertem, że operacja została ukończona pomyślnie, a wygenerowane działania będą widoczne w przyborniku po skompilowaniu projektu. Kliknij przycisk **OK**.  
  
3. Skompiluj projekt, naciskając **klawisze CTRL + SHIFT + B**, aby zaimportowane działania pojawiły się w przyborniku.  
  
4. W **Eksplorator rozwiązań**Otwórz Service1. xamlx. Usługa przepływu pracy będzie wyświetlana w projektancie.  
  
5. Wybierz działanie **sekwencji** . W okno Właściwości kliknij przycisk. **.** przycisk we właściwości **ImplementedContract** . W wyświetlonym oknie **Edytor kolekcji typów** kliknij listę rozwijaną **Typ** , a następnie wybierz pozycję **Przeglądaj w poszukiwaniu typów...** Autotekstu. W oknie dialogowym **Przeglądaj i wybierz typ platformy .NET** w obszarze  **\<bieżący projekt >** Otwórz wszystkie węzły podrzędne i wybierz pozycję **IBookService**. Kliknij przycisk **OK**. W oknie dialogowym **Edytor kolekcji typów** kliknij przycisk **OK**.  
  
6. Wybierz i Usuń działania **ReceiveRequest** i **SendResponse** .  
  
7. Z przybornika przeciągnij działanie **Buy_ReceiveAndSendReply** i **Checkout_Receive** do działania **sekwencyjnego usługi** .
