---
title: 'Instrukcje: blokowanie punktów końcowych w przedsiębiorstwie'
ms.date: 03/30/2017
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
ms.openlocfilehash: 35b9a1dbebce48823799689a581033d0483c3984
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937679"
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>Instrukcje: blokowanie punktów końcowych w przedsiębiorstwie

Duże przedsiębiorstwa często wymagają, aby aplikacje były opracowywane pod kątem zgodności z zasadami zabezpieczeń przedsiębiorstwa. W poniższych tematach omówiono sposób tworzenia i instalowania modułu sprawdzania poprawności punktu końcowego klienta, który może służyć do sprawdzania poprawności wszystkich aplikacji klienckich Windows Communication Foundation (WCF) zainstalowanych na komputerach.

W takim przypadku moduł sprawdzania poprawności jest modułem sprawdzania poprawności klienta, ponieważ to zachowanie punktu końcowego jest dodawane do sekcji [\<commonBehaviors >](../../configure-apps/file-schema/wcf/commonbehaviors.md) klienta w pliku Machine. config. Funkcja WCF ładuje typowe zachowania punktów końcowych tylko dla aplikacji klienckich i ładuje wspólne zachowania usługi tylko dla aplikacji usługi. Aby można było zainstalować ten sam moduł sprawdzania poprawności dla aplikacji usługi, moduł sprawdzania poprawności musi być zachowaniem usługi. Aby uzyskać więcej informacji, zobacz sekcję [\<commonBehaviors >](../../configure-apps/file-schema/wcf/commonbehaviors.md) .

> [!IMPORTANT]
> Zachowania usługi lub punktu końcowego nie są oznaczone atrybutem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA), które są dodawane do sekcji [\<commonBehaviors >](../../configure-apps/file-schema/wcf/commonbehaviors.md) pliku konfiguracyjnego nie są uruchamiane, gdy aplikacja działa w środowisku częściowej relacji zaufania, a w przypadku wystąpienia tego wyjątku nie jest zgłaszany żaden wyjątek. Aby wymusić uruchamianie typowych zachowań, takich jak walidatori, należy wykonać jedną z:
>
> - Oznacz wspólne zachowanie przy użyciu atrybutu <xref:System.Security.AllowPartiallyTrustedCallersAttribute>, aby można go było uruchomić w przypadku wdrożenia jako częściowo zaufanej aplikacji. Zwróć uwagę na to, że wpis rejestru można ustawić na komputerze, aby zapobiec uruchamianiu zestawów oznaczonych przez APTCA.
>
> - Upewnij się, że jeśli aplikacja jest wdrożona jako w pełni zaufana aplikacja, której użytkownicy nie mogą modyfikować ustawień zabezpieczeń dostępu kodu w celu uruchamiania aplikacji w środowisku częściowej relacji zaufania. Jeśli tak się stanie, niestandardowy moduł sprawdzania poprawności nie zostanie uruchomiony i nie zostanie zgłoszony żaden wyjątek. Aby zapewnić tę możliwość, zobacz opcja `levelfinal` przy użyciu [narzędzia zasad zabezpieczeń dostępu kodu (Caspol. exe)](../../tools/caspol-exe-code-access-security-policy-tool.md).
>
> Aby uzyskać więcej informacji, zobacz [częściowe najlepsze rozwiązania zaufania](../feature-details/partial-trust-best-practices.md) i [obsługiwane scenariusze wdrażania](../feature-details/supported-deployment-scenarios.md).

### <a name="to-create-the-endpoint-validator"></a>Aby utworzyć moduł sprawdzania poprawności punktu końcowego

1. Utwórz <xref:System.ServiceModel.Description.IEndpointBehavior> z żądanymi krokami walidacji w metodzie <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A>. Poniższy kod zawiera przykład. (`InternetClientValidatorBehavior` jest pobierana z przykładu [walidacji zabezpieczeń](../samples/security-validation.md) ).

    [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]

2. Utwórz nowe <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>, które rejestrują moduł walidacji punktu końcowego utworzony w kroku 1. Poniższy przykład kodu pokazuje to. (Oryginalny kod dla tego przykładu znajduje się w przykładowej [weryfikacji zabezpieczeń](../samples/security-validation.md) ).

    [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]

3. Upewnij się, że skompilowany zestaw jest podpisany przy użyciu silnej nazwy. Aby uzyskać szczegółowe informacje, zobacz [Narzędzie silnej nazwy (SN). EXE)](../../tools/sn-exe-strong-name-tool.md) i poleceń kompilatora dla danego języka.

### <a name="to-install-the-validator-into-the-target-computer"></a>Aby zainstalować moduł sprawdzania poprawności na komputerze docelowym

1. Zainstaluj moduł sprawdzania poprawności punktu końcowego przy użyciu odpowiedniego mechanizmu. W przedsiębiorstwie może być używane zasady grupy i Systems Management Server (SMS).

2. Zainstaluj zestaw o silnej nazwie w globalnej pamięci podręcznej zestawów przy użyciu programu [Gacutil. exe (Global Assembly Cache Tool)](../../tools/gacutil-exe-gac-tool.md).

3. Użyj <xref:System.Configuration?displayProperty=nameWithType> typów przestrzeni nazw, aby:

    1. Dodaj rozszerzenie do sekcji [\<behaviorExtensions >](../../configure-apps/file-schema/wcf/behaviorextensions.md) przy użyciu w pełni kwalifikowanej nazwy typu i Zablokuj element.

         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]

    2. Dodaj element Behavior do właściwości `EndpointBehaviors` w sekcji [\<commonBehaviors >](../../configure-apps/file-schema/wcf/commonbehaviors.md) i Zablokuj element. (Aby zainstalować moduł sprawdzania poprawności w usłudze, moduł sprawdzania poprawności musi być <xref:System.ServiceModel.Description.IServiceBehavior> i dodany do właściwości `ServiceBehaviors`). Poniższy przykład kodu pokazuje odpowiednią konfigurację po wykonaniu kroków a. i b., z wyłącznym wyjątkiem, że nie ma silnej nazwy.

        [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]

    3. Zapisz plik machine.config. Poniższy przykład kodu wykonuje wszystkie zadania w kroku 3, ale zapisuje kopię lokalnie zmodyfikowanego pliku Machine. config.

        [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, jak dodać typowe zachowanie do pliku Machine. config i zapisać kopię na dysku. `InternetClientValidatorBehavior` jest pobierana z przykładu [walidacji zabezpieczeń](../samples/security-validation.md) .

[!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]

## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework

Można również zaszyfrować elementy pliku konfiguracji. Aby uzyskać więcej informacji, zobacz sekcję Zobacz też.

## <a name="see-also"></a>Zobacz także

- [Szyfrowanie elementów pliku konfiguracji przy użyciu funkcji DPAPI](https://docs.microsoft.com/previous-versions/msp-n-p/ff647398(v=pandp.10))
- [Szyfrowanie elementów pliku konfiguracji przy użyciu RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))
