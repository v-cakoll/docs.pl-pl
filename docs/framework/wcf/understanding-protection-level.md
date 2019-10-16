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
ms.openlocfilehash: 896b75d3dfb5ebace9bef0c410e4a86dfb765bd8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321525"
---
# <a name="understanding-protection-level"></a>Omówienie poziomów ochrony

Właściwość `ProtectionLevel` znajduje się w wielu różnych klasach, takich jak <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> klas. Właściwość kontroluje, jak część (lub cała) wiadomości jest chroniona. W tym temacie objaśniono funkcję Windows Communication Foundation (WCF) i jej działanie.

Aby uzyskać instrukcje dotyczące ustawiania poziomu ochrony, zobacz [How to: Set a ProtectionLevel Property](how-to-set-the-protectionlevel-property.md).

> [!NOTE]
> Poziomy ochrony można ustawić tylko w kodzie, a nie w konfiguracji.

## <a name="basics"></a>Nazwie

Aby poznać funkcję poziomu ochrony, należy zastosować następujące podstawowe instrukcje:

- Dla dowolnej części komunikatu istnieją trzy podstawowe poziomy ochrony. Właściwość (gdziekolwiek występuje) jest ustawiona na jedną z wartości wyliczenia <xref:System.Net.Security.ProtectionLevel>. W kolejności rosnącej ochrony obejmują:

  - `None`.,

  - `Sign`., Część chroniona jest podpisana cyfrowo. Zapewnia to wykrywanie wszelkich manipulacji z częścią chronionego komunikatu.

  - `EncryptAndSign`., Część komunikatu jest zaszyfrowana, aby zapewnić poufność przed podpisaniem.

- Wymagania dotyczące ochrony można ustawić tylko dla *danych aplikacji* za pomocą tej funkcji. Na przykład nagłówki WS-Addressing są danymi infrastruktury, w związku z czym nie wpływają na `ProtectionLevel`.

- Gdy tryb zabezpieczeń ma wartość `Transport`, cała wiadomość jest chroniona przez mechanizm transportu. W związku z tym ustawienie oddzielnego poziomu ochrony dla różnych części komunikatu nie ma żadnego wpływu.

- @No__t-0 to sposób, aby deweloper ustawił *minimalny poziom* , z którym powiązanie musi być zgodne. Gdy usługa zostanie wdrożona, rzeczywiste powiązanie określone w konfiguracji może być nieobsługiwane. Na przykład domyślnie Klasa <xref:System.ServiceModel.BasicHttpBinding> nie dostarcza zabezpieczeń (chociaż można ją włączyć). W związku z tym używanie go z kontraktem, który ma dowolne ustawienie inne niż `None`, spowoduje zgłoszenie wyjątku.

- Jeśli usługa wymaga, aby minimalna wartość `ProtectionLevel` dla wszystkich komunikatów wynosi `Sign`, klient (prawdopodobnie utworzony przez technologię nieobsługującą usług WCF) może szyfrować i podpisywać wszystkie komunikaty (co jest większe niż wymagane minimum). W takim przypadku WCF nie zgłosi wyjątku, ponieważ klient ukończył więcej niż minimum. Należy jednak pamiętać, że aplikacje WCF (usługi lub klienci) nie będą w pełni zabezpieczone części wiadomości, jeśli jest to możliwe, ale będą zgodne z poziomem minimalnym. Należy również pamiętać, że w przypadku korzystania z `Transport` jako tryb zabezpieczeń, transport może nadmiernie zabezpieczyć strumień komunikatów, ponieważ nie jest on z tego względu bezpieczny na bardziej szczegółowym poziomie.

- Jeśli wartość `ProtectionLevel` jest jawnie ustawiona na `Sign` lub `EncryptAndSign`, należy użyć powiązania z włączonymi zabezpieczeniami lub wyjątek zostanie wygenerowany.

- W przypadku wybrania powiązania, które umożliwia zabezpieczenia i nie ustawisz właściwości `ProtectionLevel` w dowolnym miejscu kontraktu, wszystkie dane aplikacji zostaną zaszyfrowane i podpisane.

- W przypadku wybrania powiązania, które nie ma włączonej zabezpieczeń (na przykład Klasa `BasicHttpBinding` ma zabezpieczenia domyślnie wyłączone), a `ProtectionLevel` nie jest jawnie ustawiona, wówczas żadna z danych aplikacji nie będzie chroniona.

- Jeśli używasz powiązania, które stosuje zabezpieczenia na poziomie transportu, wszystkie dane aplikacji będą zabezpieczone zgodnie z możliwościami transportu.

- W przypadku użycia powiązania, które stosuje zabezpieczenia na poziomie komunikatu, dane aplikacji będą zabezpieczone zgodnie z poziomami ochrony ustawionymi w ramach kontraktu. Jeśli nie określisz poziomu ochrony, wszystkie dane aplikacji w komunikatach będą szyfrowane i podpisane.

- @No__t-0 można ustawić na różnych poziomach zakresu. Istnieje hierarchia skojarzona z zakresem, co zostało wyjaśnione w następnej sekcji.

## <a name="scoping"></a>Zakresów

Ustawienie `ProtectionLevel` w interfejsie API najwyższego poziomu ustawia poziom dla wszystkich poziomów poniżej. Jeśli `ProtectionLevel` zostanie ustawiona na inną wartość na niższym poziomie, wszystkie interfejsy API znajdujące się poniżej tego poziomu w hierarchii zostaną teraz zresetowane do nowego poziomu (interfejsy API powyżej, jednak nadal będą mieć wpływ na najwyższy poziom). Hierarchia jest następująca. Atrybuty na tym samym poziomie są elementami równorzędnymi.

- <xref:System.ServiceModel.ServiceContractAttribute>

- <xref:System.ServiceModel.OperationContractAttribute>

- <xref:System.ServiceModel.FaultContractAttribute>

- <xref:System.ServiceModel.MessageContractAttribute>

- <xref:System.ServiceModel.MessageHeaderAttribute>

- <xref:System.ServiceModel.MessageBodyMemberAttribute>

## <a name="programming-protectionlevel"></a>Programowanie ProtectionLevel

Aby program `ProtectionLevel` w dowolnym momencie w hierarchii, po prostu ustaw właściwość na odpowiednią wartość w przypadku zastosowania atrybutu. Aby zapoznać się z przykładami, zobacz [How to: Set Właściwość ProtectionLevel](how-to-set-the-protectionlevel-property.md).

> [!NOTE]
> Ustawienie właściwości dotyczącej błędów i kontraktów komunikatów wymaga poznania sposobu działania tych funkcji. Aby uzyskać więcej informacji, zobacz [jak: Ustawianie właściwości ProtectionLevel](how-to-set-the-protectionlevel-property.md) i [Używanie kontraktów komunikatów](./feature-details/using-message-contracts.md).

## <a name="ws-addressing-dependency"></a>Zależność WS-Addressing

W większości przypadków użycie narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wygenerowania klienta gwarantuje, że kontrakty klienta i usług są identyczne. Jednak pozornie identyczne kontrakty mogą spowodować zgłoszenie wyjątku przez klienta. Dzieje się tak, gdy powiązanie nie obsługuje specyfikacji WS-Addressing, a dla kontraktu określono wiele poziomów ochrony. Na przykład Klasa <xref:System.ServiceModel.BasicHttpBinding> nie obsługuje specyfikacji ani tworzenia niestandardowego powiązania, które nie obsługuje adresowania WS-Addressing. Funkcja `ProtectionLevel` opiera się na specyfikacji WS-Addressing, aby włączyć różne poziomy ochrony dla jednego kontraktu. Jeśli powiązanie nie obsługuje specyfikacji WS-Addressing, wszystkie poziomy zostaną ustawione na ten sam poziom ochrony. Poziom ochrony obowiązujący dla wszystkich zakresów kontraktu zostanie ustawiony na najwyższy poziom ochrony użyty w umowie.

Może to spowodować problem, który trudno debugować z pierwszego razu. Istnieje możliwość utworzenia kontraktu klienta (interfejs), który obejmuje metody dla więcej niż jednej usługi. Oznacza to, że ten sam interfejs jest używany do tworzenia klienta, który komunikuje się z wieloma usługami, a pojedynczy interfejs zawiera metody dla wszystkich usług. Deweloper musi zachować ostrożność w tym rzadkim scenariuszu, aby wywoływać tylko te metody, które mają zastosowanie do poszczególnych usług. Jeśli powiązanie jest klasą <xref:System.ServiceModel.BasicHttpBinding>, nie można obsługiwać wielu poziomów ochrony. Jednak odpowiedź usługi na klienta może odpowiedzieć na klienta z niższym poziomem ochrony niż jest to wymagane. W takim przypadku klient zgłosi wyjątek, ponieważ oczekuje wyższego poziomu ochrony.

Przykładowy kod ilustruje ten problem. W poniższym przykładzie przedstawiono usługę i kontrakt klienta. Załóżmy, że powiązanie jest elementem [\<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md) . W związku z tym wszystkie operacje na kontrakcie mają taki sam poziom ochrony. Ten jednolity poziom ochrony jest określany jako maksymalny poziom ochrony we wszystkich operacjach.

Kontrakt usługi:

[!code-csharp[c_ProtectionLevel#7](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#7)]
[!code-vb[c_ProtectionLevel#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#7)]

Poniższy kod przedstawia interfejs kontraktu klienta. Należy zauważyć, że zawiera ona metodę `Tax`, która jest przeznaczona do użycia z inną usługą:

[!code-csharp[c_ProtectionLevel#8](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#8)]
[!code-vb[c_ProtectionLevel#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#8)]

Gdy klient wywołuje metodę `Price`, zgłasza wyjątek, gdy odbierze odpowiedź od usługi. Dzieje się tak, ponieważ klient nie określa `ProtectionLevel` w `ServiceContractAttribute`, dlatego klient używa domyślnego (<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>) dla wszystkich metod, w tym metody `Price`. Jednak usługa zwraca wartość przy użyciu poziomu <xref:System.Net.Security.ProtectionLevel.Sign>, ponieważ kontrakt usługi definiuje pojedynczą metodę, która ma ustawiony poziom ochrony na <xref:System.Net.Security.ProtectionLevel.Sign>. W takim przypadku klient zgłosi błąd podczas walidacji odpowiedzi z usługi.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageHeaderAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- <xref:System.Net.Security.ProtectionLevel>
- [Zabezpieczanie usług](securing-services.md)
- [Instrukcje: ustawianie właściwości ProtectionLevel](how-to-set-the-protectionlevel-property.md)
- [Określanie i obsługa błędów w kontraktach i usługach](specifying-and-handling-faults-in-contracts-and-services.md)
- [Używanie kontraktów komunikatu](./feature-details/using-message-contracts.md)
