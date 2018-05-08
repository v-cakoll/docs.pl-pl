---
title: Korelacja na podstawie zawartości
ms.date: 03/30/2017
ms.assetid: 8638b5d6-1d59-456d-8acd-179a5b39b260
ms.openlocfilehash: b90d076d96e1bae5c44dc1c2b06f826d256f7463
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="content-based-correlation"></a>Korelacja na podstawie zawartości
W tym przykładzie przedstawiono sposób działania dotyczące komunikatów (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply>) mogą być używane z wielu correlations.and na podstawie zawartości na podstawie zawartości korelacji. W tym scenariuszu korelacji jest najpierw zainicjować na podstawie Identyfikatora zamówienia zakupu, a następnie innego korelacji jest tworzone, później oparte na identyfikator klienta. Oznacza to, jak <xref:System.ServiceModel.Activities.Receive> działania można wykonaj istniejących korelacji i inicjować korelację nowe na podstawie tego samego komunikatu przychodzącego.  
  
## <a name="demonstrates"></a>Demonstracje  
 Działania obsługi wiadomości i na podstawie zawartości korelacji  
  
## <a name="discussion"></a>Omówienie  
 Ten przykład przedstawia sposób użycia wielu korelacji na podstawie zawartości.  W tym scenariuszu korelacji jest najpierw zainicjować na podstawie Identyfikatora zamówienia zakupu, a następnie innego korelacji jest tworzone, później oparte na identyfikator klienta.  Korelacji są kaskadowych przy użyciu <xref:System.ServiceModel.Activities.Receive> działania zarówno istniejących korelacji (PurchaseOrderId) i inicjuje nowy korelacji (identyfikator klienta) oparte na ten sam komunikat przychodzący.  Aby to osiągnąć, <xref:System.ServiceModel.Activities.Receive> używa działania <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> i <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> właściwości.  
  
## <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z podwyższonym poziomem uprawnień, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikony, jak i wybierając **Uruchom jako administrator**.  
  
2.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania CascadingCorrelation.sln.  
  
3.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
4.  Aby uruchomić serwera, naciśnij klawisz F5.  
  
5.  Gdy usługa jest gotowa i nasłuchiwania dla wiadomości w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt klienta i uruchom go.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ContentBasedCorrelation`