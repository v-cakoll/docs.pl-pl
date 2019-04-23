---
title: 'Instrukcje: Tworzenie usługi przepływu pracy wykorzystującej istniejący kontrakt usługi'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: c2ca9c349718c3939d74d052ff0ed448879cd045
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344718"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>Instrukcje: Tworzenie usługi przepływu pracy wykorzystującej istniejący kontrakt usługi
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Funkcje lepszą integrację między usługami sieci web i przepływów pracy w formie Projektowanie przepływów pracy z wymogiem wcześniejszego zawarcia kontraktu. Narzędzie tworzenia przepływu pracy z wymogiem wcześniejszego zawarcia kontraktu umożliwia projektowanie najpierw kontrakt w kodzie. Narzędzie następnie automatycznie generuje szablon działania w przyborniku dla operacji w kontrakcie.  
  
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
  
1. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Importuj kontrakt usługi**. W obszarze  **\<bieżący projekt >**, otwórz wszystkie węzły podrzędne i wybierz **IBookService**. Kliknij przycisk **OK**.  
  
2. Zostanie otwarte okno dialogowe alerty, operacja ukończona pomyślnie, a które wygenerowane działania zostaną wyświetlone w przyborniku, po skompilowaniu projektu. Kliknij przycisk **OK**.  
  
3. Skompiluj projekt, naciskając klawisz **Ctrl + Shift + B**, dzięki czemu importowanych działania będą wyświetlane w przyborniku.  
  
4. W **Eksploratora rozwiązań**, otwórz Service1.xamlx. W Projektancie pojawi się usługi przepływu pracy.  
  
5. Wybierz **sekwencji** działania. W oknie dialogowym właściwości kliknij **...** znajdujący się w **ImplementedContract** właściwości. W **Editor typu Kolekce** okna, które zostanie wyświetlone, kliknij przycisk **typu** listy rozwijanej i wybierz **vyhledat typy...** wpis. W **Wyszukaj i wybierz typ architektury .NET** okna dialogowego, w obszarze  **\<bieżący projekt >**, otwórz wszystkie węzły podrzędne i wybierz **IBookService**. Kliknij przycisk **OK**. W **Editor typu Kolekce** okno dialogowe, kliknij przycisk **OK**.  
  
6. Wybierz i Usuń **ReceiveRequest** i **SendResponse** działań.  
  
7. Z przybornika przeciągnij **Buy_ReceiveAndSendReply** i **Checkout_Receive** działania na **usługa Sekwencyjna** działania.
