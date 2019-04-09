---
title: 'Instrukcje: blokowanie punktów końcowych w przedsiębiorstwie'
ms.date: 03/30/2017
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
ms.openlocfilehash: 9bfd077abf0956f014c78a7c398670822724f7e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181366"
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>Instrukcje: blokowanie punktów końcowych w przedsiębiorstwie
Dla dużych przedsiębiorstw często wymagają, że aplikacje są opracowywane zgodne z zasadami zabezpieczeń organizacji. Temacie opisano kroki umożliwiające tworzenie i instalowanie klienta weryfikacji punktu końcowego, który może służyć do sprawdzania poprawności wszystkie aplikacje klienckie usługi Windows Communication Foundation (WCF) zainstalowane na komputerach.  
  
 W tym przypadku modułu sprawdzania poprawności jest moduł weryfikacji klienta, ponieważ to zachowanie punktu końcowego jest dodawany do klienta [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) sekcji w pliku machine.config. WCF ładuje wspólnego zachowania punktu końcowego tylko dla aplikacji klienckich i ładuje wspólnego zachowania usługi tylko dla aplikacji usługi. Aby zainstalować tego samego modułu weryfikacji dla aplikacji usług, moduł weryfikacji musi być zachowania usługi. Aby uzyskać więcej informacji, zobacz [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) sekcji.  
  
> [!IMPORTANT]
>  Zachowania usługi lub punkt końcowy nie jest oznaczony atrybutem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA), które są dodawane do [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) sekcję pliku konfiguracji nie są uruchamiane, gdy aplikacja zostanie uruchomiona w częściowej relacji zaufania środowiska i żaden wyjątek jest zgłaszany w takiej sytuacji. Aby wymusić uruchomienie wspólny zbiór wykonywanych czynności takich jak moduły weryfikacji, należy:  
>   
>  --Oznacz swoje wspólnego zachowania za pomocą <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu, dzięki czemu można uruchomić, gdy wdrożony jako aplikacja częściowego zaufania. Należy pamiętać, że wpis rejestru można ustawić na komputerze, aby zapobiec oznaczone APTCA zestawy uruchamianie...  
>   
>  — Upewnij się, że jeśli aplikacja jest wdrażana jako w pełni zaufanych aplikacji, użytkownicy nie mogą modyfikować ustawienia zabezpieczeń dostępu kodu, aby uruchomić aplikację w środowisku częściowego zaufania. Jeśli tak jest, więc, niestandardowego modułu weryfikacji nie działa i nie jest zgłaszany żaden wyjątek. Jednym ze sposobów to zapewnić, można zobaczyć `levelfinal` opcji za pomocą [narzędzie zasad zabezpieczeń dostępu kodu (Caspol.exe)](https://go.microsoft.com/fwlink/?LinkId=248222).  
>   
>  Aby uzyskać więcej informacji, zobacz [częściowego zaufania najlepszych rozwiązań](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) i [obsługiwane scenariusze wdrażania](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md).  
  
### <a name="to-create-the-endpoint-validator"></a>Aby utworzyć punkt końcowy modułu sprawdzania poprawności  
  
1.  Tworzenie <xref:System.ServiceModel.Description.IEndpointBehavior> czynności żądaną sprawdzania poprawności w <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> metody. Poniższy kod zawiera przykład. ( `InternetClientValidatorBehavior` Jest pobierana z [weryfikacji zabezpieczeń](../../../../docs/framework/wcf/samples/security-validation.md) próbki.)  
  
     [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]  
  
2.  Utwórz nową <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> które rejestruje moduł weryfikacji punktu końcowego utworzonego w kroku 1. Poniższy przykład kodu pokazuje to. (Trwa oryginalny kod w tym przykładzie [weryfikacji zabezpieczeń](../../../../docs/framework/wcf/samples/security-validation.md) przykładowe.)  
  
     [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]  
  
3.  Upewnij się, że skompilowany zestaw jest podpisany silną nazwą. Aby uzyskać więcej informacji, zobacz [narzędzie silnych nazw (SN. Z rozszerzeniem EXE)](https://go.microsoft.com/fwlink/?LinkId=248217) i polecenia kompilatora dla danego języka.  
  
### <a name="to-install-the-validator-into-the-target-computer"></a>Aby zainstalować moduł weryfikacji do komputera docelowego  
  
1.  Zainstaluj punkt końcowy modułu sprawdzania poprawności, przy użyciu odpowiedniego mechanizmu. W przedsiębiorstwie to może być za pomocą zasad grupy i Systems Management Server (SMS).  
  
2.  Zainstaluj silnej nazwy zestawu w globalnej pamięci podręcznej przy użyciu [Gacutil.exe (Global Assembly Cache Tool)](../../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
3.  Użyj <xref:System.Configuration?displayProperty=nameWithType> typów w przestrzeni nazw, aby:  
  
    1.  Dodaj rozszerzenie [ \<behaviorExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md) sekcji przy użyciu w pełni kwalifikowaną nazwę typu i Zablokuj elementu.  
  
         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]  
  
    2.  Dodany element zachowanie `EndpointBehaviors` właściwość [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) sekcji, a następnie zablokować element. (Aby zainstalować moduł weryfikacji w usłudze, muszą być modułu sprawdzania poprawności <xref:System.ServiceModel.Description.IServiceBehavior> i dodane do `ServiceBehaviors` właściwości.) Poniższy przykład kodu pokazuje właściwa konfiguracja po wykonaniu kroków. i b. przy użyciu jedynym wyjątkiem, że istnieje nie silnej nazwy.  
  
         [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]  
  
    3.  Zapisz plik machine.config. Poniższy kod wykonuje wszystkie zadania w kroku 3, ale zapisuje kopię pliku machine.config zmodyfikowany lokalnie.  
  
         [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób dodawania wspólnego zachowania do pliku machine.config i Zapisz kopię na dysku. `InternetClientValidatorBehavior` Jest pobierana z [weryfikacji zabezpieczeń](../../../../docs/framework/wcf/samples/security-validation.md) próbki.  
  
 [!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Można również zaszyfrować elementy pliku konfiguracji. Aby uzyskać więcej informacji zobacz sekcję Zobacz też.  
  
## <a name="see-also"></a>Zobacz także

- [Szyfrowanie przy użyciu interfejsu DPAPI elementy pliku konfiguracji](https://go.microsoft.com/fwlink/?LinkId=94954)
- [Szyfrowanie przy użyciu RSA elementy pliku konfiguracji](https://go.microsoft.com/fwlink/?LinkId=94955)
