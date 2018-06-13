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
ms.openlocfilehash: 157e660a8b4d3866b9ab1994c409f82f16ac8359
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809784"
---
# <a name="understanding-protection-level"></a>Omówienie poziomów ochrony
`ProtectionLevel` Właściwości znajduje się na wiele różnych klas, takich jak <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> klasy. Właściwość określa, jak chronione części (lub całego) wiadomości. W tym temacie opisano funkcję Windows Communication Foundation (WCF) i jak działa.  
  
 Aby uzyskać instrukcje na temat ustawiania poziomu ochrony, zobacz [porady: Ustawianie właściwości ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md).  
  
> [!NOTE]
>  Poziomy ochrony można ustawić tylko w kodzie, nie znajduje się w konfiguracji.  
  
## <a name="basics"></a>podstawy  
 Aby zapoznać się z poziomu funkcji ochrony, zastosuj następujące instrukcje podstawowe:  
  
-   Istnieją trzy podstawowe poziomy ochrony dla dowolnej części wiadomości. Właściwość (wszędzie tam, gdzie występuje) jest ustawiona na jeden z <xref:System.Net.Security.ProtectionLevel> wartości wyliczenia. Rosnąco ochrony, obejmują:  
  
    -   `None`.  
  
    -   `Sign`. Element chroniony jest podpisany cyfrowo. Dzięki temu wykrywanie wszelkie manipulowanie części chronionej wiadomości.  
  
    -   `EncryptAndSign`. Część wiadomości są szyfrowane, aby zapewnić poufność, zanim jest podpisany.  
  
-   Można ustawić wymagania ochrony tylko w przypadku *danych aplikacji* przy użyciu tej funkcji. Na przykład WS-Addressing nagłówki są infrastruktury danych i, w związku z tym nie dotyczy `ProtectionLevel`.  
  
-   Gdy tryb zabezpieczeń jest ustawiony na `Transport`, cały komunikat jest chroniony przez mechanizm transportu. Ustawianie poziomu ochrony osobne dla różnych części komunikatu w związku z tym nie ma znaczenia.  
  
-   `ProtectionLevel` Pozwala deweloperowi ustawić *minimalny poziom* który powiązania musi być zgodne z. Po wdrożeniu usługi rzeczywistego powiązania określony w konfiguracji może lub nie może obsługiwać minimalnego poziomu. Na przykład domyślnie <xref:System.ServiceModel.BasicHttpBinding> klasy nie dostarcza zabezpieczeń (mimo że można ją włączyć). W związku z tym korzystanie z kontraktu, który zawiera wszystkie ustawienia innych niż `None` spowoduje, że wyjątek zostanie wygenerowany.  
  
-   Jeśli usługa wymaga, aby minimum `ProtectionLevel` dla wszystkich wiadomości jest `Sign`, klient (prawdopodobnie utworzone przez technologii WCF z systemem innym niż) można szyfrowania i podpisywania wszystkich wiadomości (która jest większa niż minimalna wymagana). W takim przypadku WCF nie spowoduje zgłoszenie wyjątku, ponieważ klient ma więcej niż wartość minimalna wykonywana. Należy jednak pamiętać, że aplikacje WCF (usług lub klientów) nie nadmiernie chroni części komunikatu, jeśli to możliwe, ale spełniały minimalnego poziomu. Należy również zauważyć, że przy użyciu `Transport` jako tryb zabezpieczeń transport może nadmiernie secure strumień komunikatu, ponieważ jest z założenia nie można zabezpieczyć na bardziej szczegółowym poziomie.  
  
-   Jeśli ustawisz `ProtectionLevel` jawnie na jeden `Sign` lub `EncryptAndSign`, następnie należy użyć powiązania z włączoną obsługą zabezpieczeń lub zostanie wygenerowany wyjątek.  
  
-   Po wybraniu powiązania, które zapewnia bezpieczeństwo i nie należy ustawiać `ProtectionLevel` właściwość dowolnym kontrakt wszystkich aplikacji, danych zostanie zaszyfrowana i podpisana.  
  
-   Jeśli wybierzesz powiązania, które nie ma włączoną obsługą zabezpieczeń (na przykład `BasicHttpBinding` klasa ma zabezpieczeń domyślnie wyłączone) i `ProtectionLevel` nie jest jawnie ustawiona, a następnie żadne dane aplikacji ma podlegać ochronie.  
  
-   Jeśli używasz powiązania, które dotyczą zabezpieczeń na poziomie transportu, wszystkie dane aplikacji będą chronione zgodnie z możliwościami usługi transportu.  
  
-   Użycie powiązania, które dotyczą zabezpieczeń na poziomie komunikatu danych aplikacji będą chronione zgodnie z poziomów ochrony, ustaw kontraktu. Jeśli nie określisz poziomu ochrony, a następnie wszystkie dane aplikacji w komunikatach zostanie zaszyfrowana i podpisana.  
  
-   `ProtectionLevel` Można ustawić na różnych poziomach zakresu. Brak hierarchii skojarzone z zakresu, który znajduje się w następnej sekcji.  
  
## <a name="scoping"></a>Określanie zakresu  
 Ustawienie `ProtectionLevel` na najwyższym poziomie interfejsu API, ustawia poziom na wszystkich poziomach poniżej. Jeśli `ProtectionLevel` ma ustawioną wartość inną na niższym poziomie, wszystkie interfejsy API poniżej czy poziomu w hierarchii teraz zostanie zresetowana do wartości nowy poziom (interfejsy API powyżej, jednak nadal wpływają na najwyższym poziomie). Hierarchia ma następującą składnię. Na tym samym poziomie atrybuty elementów równorzędnych.  
  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
 <xref:System.ServiceModel.FaultContractAttribute>  
  
 <xref:System.ServiceModel.MessageContractAttribute>  
  
 <xref:System.ServiceModel.MessageHeaderAttribute>  
  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
  
## <a name="programming-protectionlevel"></a>Programowanie ProtectionLevel  
 Aby program `ProtectionLevel` w dowolnym momencie w hierarchii, po prostu ustaw właściwość do odpowiedniej wartości podczas stosowania atrybutu. Aby uzyskać przykłady, zobacz [porady: Ustawianie właściwości ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md).  
  
> [!NOTE]
>  Ustawianie właściwości usterek i kontrakty wymaga zrozumienia, jak działają funkcje do wiadomości. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie właściwości ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md) i [za pomocą kontraktów komunikatu](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
## <a name="ws-addressing-dependency"></a>Protokół WS-Addressing zależności  
 W większości przypadków przy użyciu [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania klient gwarantuje, że zamówień klienta i usługi są identyczne. Pozornie identyczne kontrakty może jednak spowodować zgłoszenie wyjątku przez klienta. Dzieje się tak, gdy powiązanie nie obsługuje specyfikacji WS-Addressing i różnych poziomów ochrony są określone w umowie. Na przykład <xref:System.ServiceModel.BasicHttpBinding> klasa nie obsługuje specyfikacji lub w przypadku utworzenia niestandardowego powiązania, które nie obsługuje protokół WS-Addressing. `ProtectionLevel` Funkcji zależy od specyfikacji WS-Addressing umożliwiające różnych poziomów ochrony na pojedynczy kontrakt. Jeśli powiązanie nie obsługuje specyfikacji WS-Addressing, wszystkie poziomy zostanie ustawiona do tego samego poziomu ochrony. Poziom skuteczną ochronę dla wszystkich zakresów na kontrakt ustawi najwyższy poziom ochrony używany kontraktu.  
  
 Może to spowodować problem, który jest trudna do debugowania na pierwszy rzut oka. Istnieje możliwość tworzenia kontrakt klienta (interfejs), która zawiera metody więcej niż jedna usługa. Oznacza to, że ten sam interfejs służy do tworzenia klienta, który komunikuje się z wielu usług, a jeden interfejs zawiera metody dla wszystkich usług. Deweloper musi zajmie się w tym scenariuszu rzadkich można wywołać tylko tych metod, które są odpowiednie dla każdej określonej usługi. Jeśli wiązanie jest <xref:System.ServiceModel.BasicHttpBinding> klasy ochrony wielu poziomów nie może być obsługiwana. Jednak usługa odpowiedzi do klienta może odpowiadać klienta o niższym poziomie ochrony, niż jest to wymagane. W takim przypadku klient spowoduje zgłoszenie wyjątku, ponieważ oczekuje na wyższy poziom ochrony.  
  
 Przykładowy kod przedstawia ten problem. W poniższym przykładzie przedstawiono usługą i kontrakt klienta. Załóżmy, że powiązanie jest [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) elementu. W związku z tym wszystkie operacje na kontrakt mają taki sam poziom ochrony. Ten poziom ochrony uniform jest określana jako poziom ochrony maksymalną we wszystkich operacji.  
  
 Kontrakt usługi jest:  
  
 [!code-csharp[c_ProtectionLevel#7](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#7)]
 [!code-vb[c_ProtectionLevel#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#7)]  
  
 Poniższy kod przedstawia klienta interfejsu kontraktu. Należy pamiętać, że zawiera on `Tax` metodę, która ma być używany z innej usługi:  
  
 [!code-csharp[c_ProtectionLevel#8](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#8)]
 [!code-vb[c_ProtectionLevel#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#8)]  
  
 Kiedy klient wywołuje `Price` metoda zgłasza wyjątek po odebraniu odpowiedzi z usługi. Dzieje się tak, ponieważ klient nie określa `ProtectionLevel` na `ServiceContractAttribute`, i dlatego klient używa domyślnej (<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>) dla wszystkich metod, w tym `Price` metody. Jednak usługa zwróci wartość, przy użyciu <xref:System.Net.Security.ProtectionLevel.Sign> poziomu, ponieważ kontrakt usługi definiuje pojedynczą metodę, która ma ustawiony poziom jego ochrony <xref:System.Net.Security.ProtectionLevel.Sign>. W takim przypadku klient zgłosi błąd podczas sprawdzania poprawności odpowiedzi z usługi.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.MessageContractAttribute>  
 <xref:System.ServiceModel.MessageHeaderAttribute>  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
 <xref:System.Net.Security.ProtectionLevel>  
 [Zabezpieczanie usług](../../../docs/framework/wcf/securing-services.md)  
 [Instrukcje: ustawianie właściwości ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)  
 [Określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)  
 [Używanie kontraktów komunikatu](../../../docs/framework/wcf/feature-details/using-message-contracts.md)
