---
title: 'Instrukcje: Tworzenie kontraktu dwukierunkowego'
description: Dowiedz się, jak utworzyć umowę dupleksową, która umożliwia klientom i serwerom programu WCF wzajemne komunikowanie się ze sobą. Można inicjować wywołania do drugiego.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: 9320e5b36b8faba3602fbe1df1b95c05dcc7fa7e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247094"
---
# <a name="how-to-create-a-duplex-contract"></a>Instrukcje: Tworzenie kontraktu dwukierunkowego
W tym temacie przedstawiono podstawowe kroki tworzenia metod, które korzystają z dwukierunkowego kontraktu. Umowa dupleksowa umożliwia klientom i serwerom komunikowanie się ze sobą niezależnie, aby można było inicjować wywołania do drugiego. Umowa dupleksowa to jeden z trzech wzorców komunikatów dostępnych dla usług Windows Communication Foundation (WCF). Pozostałe dwa wzorce komunikatów to jednokierunkowe i odpowiedzi na żądanie. Umowa dupleksowa składa się z 2 1ych umów między klientem a serwerem i nie wymaga, aby wywołania metod były skorelowane. Tego rodzaju kontraktu należy używać, gdy usługa musi wysyłać zapytania do klienta, aby uzyskać więcej informacji lub jawnie podnieść zdarzenia na kliencie. Aby uzyskać więcej informacji na temat tworzenia aplikacji klienckiej dla kontraktu dupleksowego, zobacz [jak: dostęp do usług za pomocą kontraktu dupleksowego](how-to-access-services-with-a-duplex-contract.md). Aby uzyskać przykład roboczy, zobacz [dwustronny](../samples/duplex.md) przykład.  
  
### <a name="to-create-a-duplex-contract"></a>Aby utworzyć umowę dupleksową  
  
1. Utwórz interfejs, który tworzy stronę po stronie serwera umowy dupleksowej.  
  
2. Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasę do interfejsu.  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. Zadeklaruj sygnatury metod w interfejsie.  
  
4. Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasę do sygnatury każdej metody, która musi być częścią kontraktu publicznego.  
  
5. Utwórz interfejs wywołania zwrotnego, który definiuje zestaw operacji, które usługa może wywoływać na kliencie.  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. Zadeklaruj sygnatury metod w interfejsie wywołania zwrotnego.  
  
7. Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasę do sygnatury każdej metody, która musi być częścią kontraktu publicznego.  
  
8. Połącz dwa interfejsy z umową dupleksową, ustawiając <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> Właściwość w interfejsie podstawowym na typ interfejsu wywołania zwrotnego.  
  
### <a name="to-call-methods-on-the-client"></a>Aby wywołać metody na kliencie  
  
1. W implementacji usługi głównej kontraktu Zadeklaruj zmienną dla interfejsu wywołania zwrotnego.  
  
2. Ustaw zmienną na odwołanie do obiektu zwrócone przez <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> metodę <xref:System.ServiceModel.OperationContext> klasy.  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. Wywołaj metody zdefiniowane przez interfejs wywołania zwrotnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu ilustruje komunikację dupleksową. Kontrakt usługi zawiera operacje usługi do przeniesienia do przodu i do tyłu. Kontrakt klienta zawiera operację usługi do raportowania jej pozycji.  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
- Zastosowanie <xref:System.ServiceModel.ServiceContractAttribute> atrybutów i <xref:System.ServiceModel.OperationContractAttribute> umożliwia automatyczne generowanie definicji kontraktu usługi w Web Services Description Language (WSDL).  
  
- Użyj [Narzędzia do przesyłania metadanych modelu ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , aby pobrać dokument WSDL i (opcjonalnie) kod i konfigurację dla klienta.  
  
- Punkty końcowe uwidaczniające usługi dupleksowe muszą być zabezpieczone. Gdy usługa otrzymuje komunikat o dupleksie, przegląda replikę replytą w tym komunikacie przychodzącym, aby określić, gdzie należy wysłać odpowiedź. Jeśli kanał nie jest zabezpieczony, klient niezaufanego może wysłać złośliwą wiadomość z replytą maszyny docelowej, co prowadzi do odmowy usługi Maszyny docelowej. W przypadku zwykłych komunikatów z żądaniem odpowiedzi nie jest to problem, ponieważ ReplyTo jest ignorowany, a odpowiedź jest wysyłana w kanale, w którym znajduje się pierwotny komunikat.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego](how-to-access-services-with-a-duplex-contract.md)
- [Dupleks](../samples/duplex.md)
- [Projektowanie i implementowanie usług](../designing-and-implementing-services.md)
- [Instrukcje: definiowanie kontraktu usługi](../how-to-define-a-wcf-service-contract.md)
- [Sesja](../samples/session.md)
