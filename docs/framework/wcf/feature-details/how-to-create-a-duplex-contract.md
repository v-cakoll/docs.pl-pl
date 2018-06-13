---
title: 'Instrukcje: Tworzenie kontraktu dwukierunkowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: 39aea526992c503943c3f458854d09677e1b5717
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491933"
---
# <a name="how-to-create-a-duplex-contract"></a>Instrukcje: Tworzenie kontraktu dwukierunkowego
W tym temacie przedstawiono podstawowe kroki, aby utworzyć metody, które używają kontraktu dwukierunkowego (dwukierunkowe). Kontrakt dupleksu umożliwia klienci i serwery komunikować się ze sobą niezależnie, aby albo mogą inicjować połączenia do drugiego. Kontrakt dupleksu jest jednym z trzech wzorców komunikat dostępne dla usług Windows Communication Foundation (WCF). Inne dwóch komunikatów wzorce są jednokierunkowe i żądanie odpowiedź. Kontrakt dupleksowy składa się z dwóch jednokierunkowe kontraktów między klientem a serwerem i nie wymaga, aby zostać skorelowane wywołania metody. Użyj tego rodzaju kontraktu, jeśli usługa musi zapytań klienta, aby uzyskać więcej informacji, lub jawnie wywoływanie zdarzeń na kliencie. Aby uzyskać więcej informacji na temat tworzenia aplikacji klienckiej dla kontraktu dwukierunkowego, zobacz [porady: dostęp do usług z kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md). Dla przykładu pracy, zobacz [dupleksu](../../../../docs/framework/wcf/samples/duplex.md) próbki.  
  
### <a name="to-create-a-duplex-contract"></a>Aby utworzyć kontraktu dwukierunkowego  
  
1.  Utwórz interfejs, który stanowi kontrakt dupleksu po stronie serwera.  
  
2.  Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasy interfejsu.  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3.  Deklarowanie podpisy metod interfejsu.  
  
4.  Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej metody podpisie, który musi być część publicznego kontraktu.  
  
5.  Utwórz interfejs wywołania zwrotnego, który definiuje zestaw operacji, które może wywołać usługę na komputerze klienckim.  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6.  Deklarowanie sygnatury metody w interfejsie wywołania zwrotnego.  
  
7.  Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej metody podpisie, który musi być część publicznego kontraktu.  
  
8.  Połącz dwa interfejsy do kontraktu dwukierunkowego przez ustawienie <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> właściwości w podstawowy interfejs do typu interfejsu wywołania zwrotnego.  
  
### <a name="to-call-methods-on-the-client"></a>Wywoływanie metody na kliencie  
  
1.  W implementacji usługi podstawowego kontraktu należy zadeklarować zmiennej dla interfejsu wywołania zwrotnego.  
  
2.  Ustaw zmienną na odwołanie do obiektu zwrócony przez <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> metody <xref:System.ServiceModel.OperationContext> klasy.  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3.  Wywołanie metody zdefiniowane przez interfejs wywołania zwrotnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje komunikację dupleksową. Kontrakt usługi zawiera działania usługi do przenoszenia do przodu i do tyłu. Kontrakt klienta zawiera operacji usługi raportowania położenia.  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
-   Stosowanie <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> atrybuty umożliwia automatyczne generowanie definicje kontraktu usługi w sieci Web Services Description Language (WSDL).  
  
-   Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) można pobrać dokument WSDL i kodu (opcjonalne) i konfigurację klienta.  
  
-   Udostępnianie usługi dwukierunkowe punkty końcowe muszą być zabezpieczone. Gdy usługa odbiera komunikat dupleksowy, analizuje ReplyTo w tej wiadomości przychodzących, aby określić, który ma zostać wysłana odpowiedź. Jeśli kanał nie jest zabezpieczony, niezaufanego klienta może wysłać komunikat złośliwego z ReplyTo na komputerze docelowym, co może prowadzić do odmowy usługi na docelowym komputerze. Z wiadomości regularne żądanie odpowiedź to nie jest problemem, ReplyTo jest ignorowany, ponieważ odpowiedź jest wysyłana w kanale, który pierwotny komunikat pochodzi w na.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [Dupleks](../../../../docs/framework/wcf/samples/duplex.md)  
 [Projektowanie i implementowanie usług](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [Instrukcje: definiowanie kontraktu usługi](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [Sesja](../../../../docs/framework/wcf/samples/session.md)
