---
title: 'Instrukcje: tworzenie kontraktu dwukierunkowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: c00e5d8e50de89d3d4d346ccddc50282f24735b2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59332134"
---
# <a name="how-to-create-a-duplex-contract"></a>Instrukcje: tworzenie kontraktu dwukierunkowego
W tym temacie przedstawiono podstawowe kroki, aby utworzyć metody, które używają kontraktu dwukierunkowego (dwukierunkowe). Kontrakt dupleksowy umożliwia klientów i serwerów komunikować się ze sobą niezależnie, aby albo może zainicjować wywołania do drugiego. Kontraktu dwukierunkowego jest jednym z trzech wzorców komunikat dostępne dla usług Windows Communication Foundation (WCF). Komunikat innych dwa wzorce są jednokierunkowe, a "żądanie-odpowiedź". Kontrakt dupleksowy składa się z dwóch jednokierunkowe umów między klientem a serwerem i nie wymaga, aby zostać skorelowane wywołania metody. Należy użyć tego rodzaju kontraktu, podczas usługi musi zapytania klienta, aby uzyskać więcej informacji lub jawnie wywoływać zdarzenia, na komputerze klienckim. Aby uzyskać więcej informacji na temat tworzenia aplikacji klienckiej kontrakt dupleksowy, zobacz [jak: Uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md). Przykładowy pracy [dwukierunkowego](../../../../docs/framework/wcf/samples/duplex.md) próbki.  
  
### <a name="to-create-a-duplex-contract"></a>Tworzenie kontraktu dwukierunkowego  
  
1. Utwórz interfejs, tworzącą kontraktu dwukierunkowego po stronie serwera.  
  
2. Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasy interfejsu.  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. Zadeklaruj podpisy metod interfejsu.  
  
4. Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy, aby każdy podpis metody, który musi być częścią publicznego kontraktu.  
  
5. Utwórz interfejs wywołania zwrotnego, który definiuje zestaw operacji, które można wywołać usługę na komputerze klienckim.  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. Zadeklaruj podpisy metod w interfejs wywołania zwrotnego.  
  
7. Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy, aby każdy podpis metody, który musi być częścią publicznego kontraktu.  
  
8. Łączenie dwóch interfejsów w kontrakt dupleksowy, ustawiając <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> właściwość podstawowy interfejs do typu interfejs wywołania zwrotnego.  
  
### <a name="to-call-methods-on-the-client"></a>Wywoływanie metod na komputerze klienckim  
  
1. W implementacji usługi podstawowego kontraktu należy zadeklarować zmienną interfejs wywołania zwrotnego.  
  
2. Ustaw zmienną na zwracane przez odwołanie do obiektu <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> metody <xref:System.ServiceModel.OperationContext> klasy.  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. Wywołanie metody zdefiniowane przez interfejs wywołania zwrotnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje komunikację dupleksową. Kontrakt usługi zawiera operacje usługi do przenoszenia do przodu i do tyłu. Umowy klienta zawiera operacji usługi raportowania położenia.  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
-   Stosowanie <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> atrybuty umożliwia automatyczne generowanie definicje kontraktu usługi w sieci Web Services Description Language (WSDL).  
  
-   Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do pobrania dokumentu WSDL i (opcjonalnie) kod i konfiguracja dla klientów.  
  
-   Udostępnianie usługi dwukierunkowe punkty końcowe muszą być zabezpieczone. Gdy usługa odbiera komunikat dwukierunkowego, analizuje ReplyTo w tej wiadomości przychodzących, aby określić, gdzie wysyłać odpowiedzi. Jeśli kanał nie jest zabezpieczony, niezaufanego klienta można wysyłanie wiadomości złośliwego z ReplyTo maszynę docelową, co prowadzi do typu "odmowa usługi maszyny docelowej". Przy użyciu komunikatów regularne "żądanie-odpowiedź" to nie jest problemem, ponieważ ReplyTo jest ignorowana, a odpowiedź jest wysyłana na kanale, który oryginalnego komunikatu materiał na.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Dupleks](../../../../docs/framework/wcf/samples/duplex.md)
- [Projektowanie i implementowanie usług](../../../../docs/framework/wcf/designing-and-implementing-services.md)
- [Instrukcje: Definiowanie kontraktu usługi](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [Sesja](../../../../docs/framework/wcf/samples/session.md)
