---
title: Korelacja na podstawie zawartości
ms.date: 03/30/2017
ms.assetid: 8638b5d6-1d59-456d-8acd-179a5b39b260
ms.openlocfilehash: c0367f480701468dcd5024ea3439bdcd38acc78f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731725"
---
# <a name="content-based-correlation"></a>Korelacja na podstawie zawartości
W tym przykładzie przedstawiono sposób działania dotyczące komunikatów (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply>) mogą być używane z wielu correlations.and na podstawie zawartości na podstawie zawartości korelacji. W tym scenariuszu korelacja najpierw jest inicjowana na podstawie Identyfikatora zamówienia zakupu, a następnie inny korelacji jest tworzone, później oparciu o identyfikator klienta. To pokazuje jak <xref:System.ServiceModel.Activities.Receive> działania mogą postępuj zgodnie z istniejących korelacji i zainicjować nową korelację na podstawie tego samego komunikatu przychodzącego.  
  
## <a name="demonstrates"></a>Demonstracje  
 Działań dotyczących komunikatów i korelacji na podstawie zawartości  
  
## <a name="discussion"></a>Dyskusja  
 W tym przykładzie pokazano, jak używać wielu korelacje na podstawie zawartości.  W tym scenariuszu korelacja najpierw jest inicjowana na podstawie Identyfikatora zamówienia zakupu, a następnie inny korelacji jest tworzone, później oparciu o identyfikator klienta.  Korelacji są kaskadowy, za pomocą <xref:System.ServiceModel.Activities.Receive> działanie, które następuje istniejących korelacji (PurchaseOrderId) i inicjuje nową korelację (identyfikator klienta) na podstawie tego samego przychodzącego komunikatu.  Aby to osiągnąć, <xref:System.ServiceModel.Activities.Receive> używa działania <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> i <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> właściwości.  
  
## <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z podwyższonym poziomem uprawnień, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonę i wybierając polecenie **Uruchom jako administrator**.  
  
2.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania CascadingCorrelation.sln.  
  
3.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
4.  Aby uruchomić serwer, naciśnij klawisz F5.  
  
5.  Gdy usługa jest gotowy i nasłuchuje komunikatów w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt klienta, a następnie uruchom go.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ContentBasedCorrelation`