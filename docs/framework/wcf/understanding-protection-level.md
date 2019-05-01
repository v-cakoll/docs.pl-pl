---
title: Omówienie poziomów ochrony
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 0c034608-a1ac-4007-8287-b1382eaa8bf2
ms.openlocfilehash: 90fb844931c3af54367d0e7c14a766636cdcc71a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791433"
---
# <a name="understanding-protection-level"></a>Omówienie poziomów ochrony
`ProtectionLevel` Właściwość znajduje się na wiele różnych klas, takie jak <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> klasy. Właściwość kontroluje, jak jest chroniona część (lub całość) wiadomości. W tym temacie opisano funkcję Windows Communication Foundation (WCF) i jak działa.  
  
 Aby uzyskać instrukcje na temat ustawiania poziomu ochrony, zobacz [jak: Ustawianie właściwości ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md).  
  
> [!NOTE]
>  Poziomy ochrony można ustawić tylko w przypadku kodu nie znajduje się w konfiguracji.  
  
## <a name="basics"></a>Podstawy  
 Aby zrozumieć funkcję poziomu ochrony, mają zastosowanie następujące instrukcje podstawowe:  
  
- Trzy podstawowe poziomy ochrony istnieją dla dowolnej części wiadomości. Właściwości (wszędzie tam, gdzie występuje) jest ustawiona na jedną z <xref:System.Net.Security.ProtectionLevel> wartości wyliczenia. Rosnąco ochrony, ulepszenia obejmują:  
  
    - `None`.  
  
    - `Sign`. Część chroniony jest podpisany cyfrowo. Dzięki temu wykrywanie wszelkie manipulowanie część chronionej wiadomości.  
  
    - `EncryptAndSign`. Część wiadomości jest szyfrowany do zapewnienia poufności, zanim jest podpisany.  
  
- Możesz ustawić wymagania dotyczące ochrony tylko w przypadku *dane aplikacji* za pomocą tej funkcji. Na przykład nagłówków WS-Addressing dane infrastruktury i, w związku z tym, nie dotyczy `ProtectionLevel`.  
  
- Gdy tryb zabezpieczeń jest ustawiony na `Transport`, cała wiadomość jest chroniona przez mechanizm transportu. W związku z tym ustawienie poziomu ochrony oddzielnych dla różnych części komunikatu nie ma znaczenia.  
  
- `ProtectionLevel` Sposób dla deweloperów ustawić *minimalny poziom* , powiązania musi być zgodne. Po wdrożeniu usługi faktycznego wiązania określony w konfiguracji może być lub może nie obsługiwać minimalny poziom. Na przykład domyślnie <xref:System.ServiceModel.BasicHttpBinding> klasy nie dostarcza zabezpieczeń (mimo że można ją włączyć). W związku z tym, za pomocą za pomocą kontraktu, który ma dowolnym ustawienie inne niż `None` spowoduje zgłoszenie wyjątku.  
  
- Jeśli usługa wymaga, aby minimum `ProtectionLevel` dla wszystkich wiadomości jest `Sign`, klient (może być utworzona przez technologii WCF bez) można szyfrowanie i podpisywanie wszystkich wiadomości (czyli jest większa niż minimalna wymagana). W tym przypadku WCF nie spowoduje zgłoszenie wyjątku, ponieważ klient ma więcej niż wartość minimalna gotowe. Należy jednak pamiętać, że aplikacji WCF (usług lub klientów) nie nadmiernie zabezpieczy część wiadomości, jeśli jest to możliwe, ale będą musiały spełniać minimalny poziom. Należy również zauważyć, że podczas korzystania `Transport` jako tryb zabezpieczeń transport może nadmiernie zabezpieczenia strumienia komunikatów ponieważ natury nie może zabezpieczyć na bardziej szczegółowym poziomie.  
  
- Jeśli ustawisz `ProtectionLevel` jawnie na wartość `Sign` lub `EncryptAndSign`, konieczne jest użycie powiązanie z włączonymi zabezpieczeniami lub zostanie zgłoszony wyjątek.  
  
- Po wybraniu powiązanie, które zapewnia bezpieczeństwo i nie należy ustawiać `ProtectionLevel` właściwość dowolne miejsce na kontrakt wszystkich aplikacji, danych zostanie zaszyfrowana i podpisana.  
  
- W przypadku wybrania powiązania, który nie ma włączoną obsługą zabezpieczeń (na przykład `BasicHttpBinding` klasa ma domyślnie wyłączone zabezpieczeń), a `ProtectionLevel` nie jest jawnie określona, a następnie żadne dane aplikacji będą chronione.  
  
- Jeśli używasz powiązanie, które mają zastosowanie zabezpieczeń na poziomie transportu, wszystkie dane aplikacji zostanie zabezpieczone zgodnie z możliwości transportu.  
  
- Jeśli używasz powiązanie, które mają zastosowanie zabezpieczeń na poziomie komunikatu, dane aplikacji zostanie zabezpieczone zgodnie z poziomów ochrony, ustaw w umowie. Jeśli nie określisz poziom ochrony, a następnie wszystkie dane aplikacji w komunikatach zostanie zaszyfrowana i podpisana.  
  
- `ProtectionLevel` Można ustawić na różnych poziomach zakresu. Brak hierarchii skojarzone z zakresu, które wyjaśniono w następnej sekcji.  
  
## <a name="scoping"></a>Wyznaczanie zakresu  
 Ustawienie `ProtectionLevel` na najwyższym poziomie interfejsu API ustawia poziom na wszystkich poziomach poniżej. Jeśli `ProtectionLevel` jest ustawiona na inną wartość na niższym poziomie, wszystkie interfejsy API poniżej, poziom w hierarchii spowoduje zresetowanie teraz nowy poziom (interfejsy API powyżej, ale nadal będzie miało wpływ na najwyższym poziomie). Hierarchia jest w następujący sposób. Atrybuty na tym samym poziomie są elementami równorzędnymi.  
  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
 <xref:System.ServiceModel.FaultContractAttribute>  
  
 <xref:System.ServiceModel.MessageContractAttribute>  
  
 <xref:System.ServiceModel.MessageHeaderAttribute>  
  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
  
## <a name="programming-protectionlevel"></a>Programowanie ProtectionLevel  
 Aby program `ProtectionLevel` w dowolnym momencie w hierarchii, wystarczy ustawić dla właściwości do odpowiedniej wartości podczas stosowania atrybutu. Aby uzyskać przykłady, zobacz [jak: Ustawianie właściwości ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md).  
  
> [!NOTE]
>  Ustawianie właściwości na błędy i komunikat kontraktów wymaga zrozumienia, jak działają te funkcje. Aby uzyskać więcej informacji, zobacz [jak: Ustawianie właściwości ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md) i [używanie kontraktów komunikatu](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
## <a name="ws-addressing-dependency"></a>WS-Addressing zależności  
 W większości przypadków przy użyciu [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) wygenerować klienta zapewnia się, że zamówień klienta i usługi są identyczne. Pozornie identyczne kontraktów może jednak spowodować zgłoszenie wyjątku przez klienta. Dzieje się tak, zawsze wtedy, gdy powiązanie nie obsługuje specyfikacji WS-Addressing i wiele poziomów ochrony są określone w umowie. Na przykład <xref:System.ServiceModel.BasicHttpBinding> klasa nie obsługuje specyfikacji lub w przypadku utworzenia niestandardowego powiązania, które obsługuje WS-Addressing. `ProtectionLevel` Funkcji zależy od specyfikacji WS-Addressing umożliwiające różnych poziomów ochrony na jednej umowy. Jeśli wiązanie nie obsługuje specyfikacji WS-Addressing, zostaną ustawione na wszystkich poziomach do tego samego poziomu ochrony. Poziom skuteczną ochronę dla wszystkich zakresów na kontrakt ustawi najwyższy poziom ochrony używane w umowie.  
  
 Może to spowodować problem, który jest trudny do debugowania na pierwszy rzut oka. Istnieje możliwość tworzenia kontraktu klienta (interfejs), który zawiera metody, aby uzyskać więcej niż jedna usługa. Oznacza to, że ten sam interfejs umożliwiający utworzenie klienta, który komunikuje się z wieloma usługami, a jeden interfejs zawiera metody dla wszystkich usług. Deweloper musi powinien zachować ostrożność, w tym scenariuszu rzadkich do wywołania tych metod, które są odpowiednie dla każdej określonej usługi. Jeśli wiązanie jest <xref:System.ServiceModel.BasicHttpBinding> klasy ochrony wielu poziomów nie są obsługiwane. Jednak usługa odpowiadania na kliencie może odpowiadać klienta o niższym poziomie ochrony, niż jest to wymagane. W takim przypadku klient spowoduje zgłoszenie wyjątku, ponieważ oczekuje wyższego poziomu ochrony.  
  
 Przykład kodu ilustruje ten problem. Poniższy przykład pokazuje usługi i umowy klienta. Przyjęto założenie, że powiązanie jest [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) elementu. Wszystkie operacje na kontrakt więc ten sam poziom ochrony. Ten poziom ochrony jednolitego jest określana jako poziom maksymalną ochronę we wszystkich operacjach.  
  
 Kontrakt usługi to:  
  
 [!code-csharp[c_ProtectionLevel#7](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#7)]
 [!code-vb[c_ProtectionLevel#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#7)]  
  
 Poniższy kod przedstawia klienta interfejsu kontraktu. Należy zauważyć, że zawiera on `Tax` metodę, która jest przeznaczona do użycia z innej usługi:  
  
 [!code-csharp[c_ProtectionLevel#8](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#8)]
 [!code-vb[c_ProtectionLevel#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#8)]  
  
 Kiedy klient wywołuje `Price` metody go zgłasza wyjątek, gdy odbiera odpowiedź z usługi. Dzieje się tak, ponieważ klient nie ma określonego `ProtectionLevel` na `ServiceContractAttribute`, i w związku z tym klient używa domyślnego (<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>) dla wszystkich metod, takich jak `Price` metody. Jednak usługa zwraca wartość, przy użyciu <xref:System.Net.Security.ProtectionLevel.Sign> poziomu, ponieważ kontrakt usługi określa pojedynczą metodę, która ma swojego poziomu ochrony, ustaw <xref:System.Net.Security.ProtectionLevel.Sign>. W takim przypadku klient będzie sygnalizować błąd, podczas sprawdzania poprawności odpowiedzi z usługi.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageHeaderAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- <xref:System.Net.Security.ProtectionLevel>
- [Zabezpieczanie usług](../../../docs/framework/wcf/securing-services.md)
- [Instrukcje: Ustawianie właściwości ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)
- [Określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Używanie kontraktów komunikatu](../../../docs/framework/wcf/feature-details/using-message-contracts.md)
