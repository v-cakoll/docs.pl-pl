---
title: "Porady: blokowanie punktów końcowych w przedsiębiorstwie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ada33c6b6ea0995d0390040710ed1b2457b9e4af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>Porady: blokowanie punktów końcowych w przedsiębiorstwie
Duże przedsiębiorstwa często wymagają, że aplikacje są tworzone zgodnie z zasadami zabezpieczeń organizacji. Następującym temacie omówiono sposób rozwijać i zainstalować moduł weryfikacji punktu końcowego klienta używany do sprawdzania poprawności wszystkich [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacje klienckie instalowane na komputerach.  
  
 W takim przypadku modułu sprawdzania poprawności jest moduł weryfikacji klienta, ponieważ to zachowanie punktu końcowego zostanie dodany do klienta [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) sekcji w pliku machine.config. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ładuje wspólnego zachowania punktu końcowego tylko dla aplikacji klienckich i ładuje wspólnego zachowania usługi tylko dla aplikacji usługi. Aby zainstalować tego samego modułu weryfikacji dla aplikacji usług, modułu sprawdzania poprawności musi być zachowanie usługi. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) sekcji.  
  
> [!IMPORTANT]
>  Zachowania usługi lub punkt końcowy nie jest oznaczony atrybutem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA), które są dodawane do [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) sekcji pliku konfiguracji nie są uruchamiane, gdy aplikacja działa w częściowej relacji zaufania środowisko i żaden wyjątek jest zgłaszany w takiej sytuacji. Aby wymusić uruchamianie zachowań wspólnych, takie jak moduły weryfikacji, należy:  
>   
>  --Oznaczyć z typowych zachowanie w przypadku <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu, dzięki czemu można uruchamiać, gdy wdrożony jako aplikacja zaufania częściowego. Należy pamiętać, że wpis rejestru można ustawić na komputerze, aby zapobiec oznaczone atrybutem APTCA zestawy uruchamianie...  
>   
>  — Upewnij się, że jeśli aplikacja jest wdrażana jako aplikacja całkowicie zaufane, że użytkownicy nie mogą modyfikować ustawienia zabezpieczeń dostępu kodu do uruchomienia aplikacji w środowisku zaufania częściowego. Mogą one to robić, niestandardowego modułu weryfikacji nie działa, a nie wyjątek. Jednym ze sposobów to zapewnić, aby zapoznać `levelfinal` opcję przy użyciu [narzędzie zasad zabezpieczenia dostępu kodu (Caspol.exe)](http://go.microsoft.com/fwlink/?LinkId=248222).  
>   
>  Aby uzyskać więcej informacji, zobacz [częściowego zaufania najlepsze rozwiązania w zakresie](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) i [obsługiwane scenariusze wdrażania](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md).  
  
### <a name="to-create-the-endpoint-validator"></a>Aby utworzyć punkt końcowy modułu sprawdzania poprawności  
  
1.  Utwórz <xref:System.ServiceModel.Description.IEndpointBehavior> kroków żądaną weryfikacji w <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> metody. Poniższy kod stanowi przykład. ( `InternetClientValidatorBehavior` Jest pobierana z [walidacji](../../../../docs/framework/wcf/samples/security-validation.md) próbki.)  
  
     [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]  
  
2.  Utwórz nowe <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> który rejestruje punkt końcowy modułu sprawdzania poprawności, utworzony w kroku 1. Poniższy przykład kodu pokazuje to. (Oryginalny kod w tym przykładzie jest [walidacji](../../../../docs/framework/wcf/samples/security-validation.md) próbki.)  
  
     [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]  
  
3.  Upewnij się, że skompilowany zestaw jest podpisany przy użyciu silnej nazwy. Aby uzyskać więcej informacji, zobacz [silnej nazwy narzędzia (SN. Wywołanie pliku EXE)](http://go.microsoft.com/fwlink/?LinkId=248217) i polecenia kompilatora dla danego języka.  
  
### <a name="to-install-the-validator-into-the-target-computer"></a>Aby zainstalować moduł weryfikacji do komputera docelowego  
  
1.  Zainstaluj moduł weryfikacji punktu końcowego przy użyciu mechanizmu odpowiednie. W przedsiębiorstwie to może być za pomocą zasad grupy i Systems Management Server (SMS).  
  
2.  Zainstaluj zestaw o silnej nazwie w przy użyciu pamięci podręcznej GAC [Gacutil.exe (narzędzie globalnej pamięci podręcznej zestawów)](http://msdn.microsoft.com/library/ex0ss12c\(v=vs.110\).aspx).  
  
3.  Użyj <xref:System.Configuration?displayProperty=nameWithType> przestrzeni nazw typów, aby:  
  
    1.  Dodaj rozszerzenie do [ \<behaviorExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md) sekcji przy użyciu nazwy typu w pełni kwalifikowaną i Zablokuj element.  
  
         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]  
  
    2.  Dodany element zachowanie `EndpointBehaviors` właściwość [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) sekcji i Zablokuj element. (Aby zainstalować moduł weryfikacji w usłudze, musi być modułu sprawdzania poprawności <xref:System.ServiceModel.Description.IServiceBehavior> i dodane do `ServiceBehaviors` właściwości.) Poniższy przykład kodu pokazuje właściwej konfiguracji po wykonaniu kroków. i b. z jedynym wyjątkiem, że istnieje bez silnej nazwy.  
  
         [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]  
  
    3.  Zapisz plik machine.config. Poniższy przykład kodu wykonuje wszystkie zadania w kroku 3, ale powoduje zapisanie kopii pliku machine.config zmodyfikowanej lokalnie.  
  
         [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób dodawania wspólnego zachowania w pliku machine.config i zapisać kopię na dysku. `InternetClientValidatorBehavior` Jest pobierana z [walidacji](../../../../docs/framework/wcf/samples/security-validation.md) próbki.  
  
 [!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Można również zaszyfrować elementy pliku konfiguracji. Aby uzyskać więcej informacji zobacz sekcję Zobacz też.  
  
## <a name="see-also"></a>Zobacz też  
 [Szyfrowanie przy użyciu DPAPI elementy pliku konfiguracji](http://go.microsoft.com/fwlink/?LinkId=94954)  
 [Szyfrowanie przy użyciu RSA elementy pliku konfiguracji](http://go.microsoft.com/fwlink/?LinkId=94955)
