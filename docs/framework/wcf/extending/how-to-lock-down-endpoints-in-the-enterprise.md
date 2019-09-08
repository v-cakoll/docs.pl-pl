---
title: 'Instrukcje: blokowanie punktów końcowych w przedsiębiorstwie'
ms.date: 03/30/2017
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
ms.openlocfilehash: fb9232c98f672701c60fa9228bb34d7b24d52330
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796965"
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>Instrukcje: blokowanie punktów końcowych w przedsiębiorstwie

Duże przedsiębiorstwa często wymagają, aby aplikacje były opracowywane pod kątem zgodności z zasadami zabezpieczeń przedsiębiorstwa. W poniższych tematach omówiono sposób tworzenia i instalowania modułu sprawdzania poprawności punktu końcowego klienta, który może służyć do sprawdzania poprawności wszystkich aplikacji klienckich Windows Communication Foundation (WCF) zainstalowanych na komputerach.

W takim przypadku moduł sprawdzania poprawności jest modułem sprawdzania poprawności klienta, ponieważ to zachowanie punktu końcowego jest dodawane do sekcji [ \<> CommonBehaviors](../../configure-apps/file-schema/wcf/commonbehaviors.md) klienta w pliku Machine. config. Funkcja WCF ładuje typowe zachowania punktów końcowych tylko dla aplikacji klienckich i ładuje wspólne zachowania usługi tylko dla aplikacji usługi. Aby można było zainstalować ten sam moduł sprawdzania poprawności dla aplikacji usługi, moduł sprawdzania poprawności musi być zachowaniem usługi. Aby uzyskać więcej informacji, zobacz [ \<sekcję > CommonBehaviors](../../configure-apps/file-schema/wcf/commonbehaviors.md) .

> [!IMPORTANT]
> Zachowania usługi lub punktu końcowego nie są oznaczone <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutem (APTCA), które są dodawane [ \<do sekcji CommonBehaviors >](../../configure-apps/file-schema/wcf/commonbehaviors.md) pliku konfiguracji nie są uruchamiane, gdy aplikacja działa w środowisku częściowego zaufania, a nie wyjątek jest zgłaszany w przypadku wystąpienia tego problemu. Aby wymusić uruchamianie typowych zachowań, takich jak walidatori, należy wykonać jedną z:
>
> - Oznacz wspólne zachowanie przy użyciu <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu, aby można go było uruchomić w przypadku wdrożenia jako częściowo zaufanej aplikacji. Zwróć uwagę na to, że wpis rejestru można ustawić na komputerze, aby zapobiec uruchamianiu zestawów oznaczonych przez APTCA.
>
> - Upewnij się, że jeśli aplikacja jest wdrożona jako w pełni zaufana aplikacja, której użytkownicy nie mogą modyfikować ustawień zabezpieczeń dostępu kodu w celu uruchamiania aplikacji w środowisku częściowej relacji zaufania. Jeśli tak się stanie, niestandardowy moduł sprawdzania poprawności nie zostanie uruchomiony i nie zostanie zgłoszony żaden wyjątek. Aby zapewnić tę możliwość, zobacz `levelfinal` opcję używanie [narzędzia zasad zabezpieczeń dostępu kodu (Caspol. exe)](https://go.microsoft.com/fwlink/?LinkId=248222).
>
> Aby uzyskać więcej informacji, zobacz [częściowe najlepsze rozwiązania zaufania](../feature-details/partial-trust-best-practices.md) i [obsługiwane scenariusze wdrażania](../feature-details/supported-deployment-scenarios.md).

### <a name="to-create-the-endpoint-validator"></a>Aby utworzyć moduł sprawdzania poprawności punktu końcowego

1. Utwórz element <xref:System.ServiceModel.Description.IEndpointBehavior> z żądanymi krokami walidacji <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> w metodzie. Poniższy kod zawiera przykład. (Jest pobierany z przykładu [weryfikacji zabezpieczeń).](../samples/security-validation.md) `InternetClientValidatorBehavior`

    [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]

2. Utwórz nowy <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> , który rejestruje moduł walidacji punktu końcowego utworzony w kroku 1. Poniższy przykład kodu pokazuje to. (Oryginalny kod dla tego przykładu znajduje się w przykładowej [weryfikacji zabezpieczeń](../samples/security-validation.md) ).

    [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]

3. Upewnij się, że skompilowany zestaw jest podpisany przy użyciu silnej nazwy. Aby uzyskać szczegółowe informacje, zobacz [Narzędzie silnej nazwy (SN). EXE)](https://go.microsoft.com/fwlink/?LinkId=248217) i poleceń kompilatora dla danego języka.

### <a name="to-install-the-validator-into-the-target-computer"></a>Aby zainstalować moduł sprawdzania poprawności na komputerze docelowym

1. Zainstaluj moduł sprawdzania poprawności punktu końcowego przy użyciu odpowiedniego mechanizmu. W przedsiębiorstwie może być używane zasady grupy i Systems Management Server (SMS).

2. Zainstaluj zestaw o silnej nazwie w globalnej pamięci podręcznej zestawów przy użyciu programu [Gacutil. exe (Global Assembly Cache Tool)](../../tools/gacutil-exe-gac-tool.md).

3. Użyj typów <xref:System.Configuration?displayProperty=nameWithType> przestrzeni nazw, aby:

    1. Dodaj rozszerzenie do [ \<sekcji BehaviorExtensions >](../../configure-apps/file-schema/wcf/behaviorextensions.md) przy użyciu w pełni kwalifikowanej nazwy typu i Zablokuj element.

         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]

    2. Dodaj element Behavior do `EndpointBehaviors` właściwości [ \<CommonBehaviors >](../../configure-apps/file-schema/wcf/commonbehaviors.md) i Zablokuj element. (Aby zainstalować moduł sprawdzania poprawności w usłudze, moduł sprawdzania poprawności musi być <xref:System.ServiceModel.Description.IServiceBehavior> i dodany `ServiceBehaviors` do właściwości). Poniższy przykład kodu pokazuje odpowiednią konfigurację po wykonaniu kroków a. i b., z wyłącznym wyjątkiem, że nie ma silnej nazwy.

        [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]

    3. Zapisz plik machine.config. Poniższy przykład kodu wykonuje wszystkie zadania w kroku 3, ale zapisuje kopię lokalnie zmodyfikowanego pliku Machine. config.

        [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, jak dodać typowe zachowanie do pliku Machine. config i zapisać kopię na dysku. Jest pobierana z przykładu [weryfikacji zabezpieczeń.](../samples/security-validation.md) `InternetClientValidatorBehavior`

[!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework

Można również zaszyfrować elementy pliku konfiguracji. Aby uzyskać więcej informacji, zobacz sekcję Zobacz też.

## <a name="see-also"></a>Zobacz także

- [Szyfrowanie elementów pliku konfiguracji przy użyciu funkcji DPAPI](https://go.microsoft.com/fwlink/?LinkId=94954)
- [Szyfrowanie elementów pliku konfiguracji przy użyciu RSA](https://go.microsoft.com/fwlink/?LinkId=94955)
