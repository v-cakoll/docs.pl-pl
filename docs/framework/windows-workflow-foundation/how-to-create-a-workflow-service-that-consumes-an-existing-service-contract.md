---
title: 'Instrukcje: Tworzenie usługi przepływu pracy wykorzystującej istniejący kontrakt usługi'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 82c9ccc21600ae0b9ff8c514a51ec9b97f8f1d37
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378128"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>Instrukcje: Tworzenie usługi przepływu pracy wykorzystującej istniejący kontrakt usługi
Funkcje programu .NET framework 4.5 lepszą integrację między usługami sieci web i przepływów pracy w formie Projektowanie przepływów pracy z wymogiem wcześniejszego zawarcia kontraktu. Narzędzie tworzenia przepływu pracy z wymogiem wcześniejszego zawarcia kontraktu umożliwia projektowanie najpierw kontrakt w kodzie. Narzędzie następnie automatycznie generuje szablon działania w przyborniku dla operacji w kontrakcie.  
  
> [!NOTE]
>  Ten temat zawiera wskazówki krok po kroku dotyczące tworzenia przepływu pracy z wymogiem wcześniejszego zawarcia kontraktu usługi. Aby uzyskać więcej informacji na temat programowanie usługi przepływu pracy z wymogiem wcześniejszego zawarcia kontraktu, zobacz [kontraktu pierwszy programowanie usługi przepływu pracy](contract-first-workflow-service-development.md).  
  
### <a name="creating-the-workflow-project"></a>Tworzenie projektu przepływu pracy  
  
1. W programie Visual Studio, wybierz **pliku**, **nowy projekt**. Wybierz **WCF** węźle **C#** w węźle **szablony** drzewa, a następnie wybierz **aplikacja usługi przepływu pracy WCF** szablon.  
  
2. Nazwa nowego projektu `ContractFirst` i kliknij przycisk **Ok**.  
  
### <a name="creating-the-service-contract"></a>Tworzenie kontraktu usługi  
  
1. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element...** . Wybierz **kodu** węzła po lewej stronie, a **klasy** szablonu po prawej stronie. Nadaj nowej klasie `IBookService` i kliknij przycisk **Ok**.  
  
2. W górnej części okna kodu, który pojawia się, Dodaj instrukcję Using do `System.Servicemodel`.  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3. Zmień definicję klasy przykładowe następująca definicja interfejsu.  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. Skompiluj projekt, naciskając klawisz **Ctrl + Shift + B**.  
  
### <a name="importing-the-service-contract"></a>Trwa importowanie kontraktu usługi  
  
1. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Importuj kontrakt usługi**. W obszarze  **\<bieżący projekt >** , otwórz wszystkie węzły podrzędne i wybierz **IBookService**. Kliknij przycisk **OK**.  
  
2. Zostanie otwarte okno dialogowe alerty, operacja ukończona pomyślnie, a które wygenerowane działania zostaną wyświetlone w przyborniku, po skompilowaniu projektu. Kliknij przycisk **OK**.  
  
3. Skompiluj projekt, naciskając klawisz **Ctrl + Shift + B**, dzięki czemu importowanych działania będą wyświetlane w przyborniku.  
  
4. W **Eksploratora rozwiązań**, otwórz Service1.xamlx. W Projektancie pojawi się usługi przepływu pracy.  
  
5. Wybierz **sekwencji** działania. W oknie dialogowym właściwości kliknij **...** znajdujący się w **ImplementedContract** właściwości. W **Editor typu Kolekce** okna, które zostanie wyświetlone, kliknij przycisk **typu** listy rozwijanej i wybierz **vyhledat typy...** wpis. W **Wyszukaj i wybierz typ architektury .NET** okna dialogowego, w obszarze  **\<bieżący projekt >** , otwórz wszystkie węzły podrzędne i wybierz **IBookService**. Kliknij przycisk **OK**. W **Editor typu Kolekce** okno dialogowe, kliknij przycisk **OK**.  
  
6. Wybierz i Usuń **ReceiveRequest** i **SendResponse** działań.  
  
7. Z przybornika przeciągnij **Buy_ReceiveAndSendReply** i **Checkout_Receive** działania na **usługa Sekwencyjna** działania.
