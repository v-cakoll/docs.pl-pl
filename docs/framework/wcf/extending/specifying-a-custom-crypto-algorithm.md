---
title: "Określanie niestandardowego algorytmu kryptograficznego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 630457e4d1b30fe2a9439c3a41af5da92606c55a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-a-custom-crypto-algorithm"></a>Określanie niestandardowego algorytmu kryptograficznego
Usługi WCF pozwala określić niestandardowy algorytm kryptograficzny do użycia podczas szyfrowania danych lub obliczeniowych podpisów cyfrowych. Można to zrobić przez następujące kroki:  
  
1.  Klasa wyprowadzona z<xref:System.ServiceModel.Security.SecurityAlgorithmSuite>  
  
2.  Rejestrowanie algorytmu  
  
3.  Konfigurowanie powiązania o <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-klasy.  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a>Wyprowadzenia klasy z SecurityAlgorithmSuite  
 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> Jest abstrakcyjna klasa podstawowa, która pozwala na Określanie algorytmu do użycia podczas wykonywania zabezpieczeń różnych operacji związanych z. Na przykład obliczania skrótu podpisu cyfrowego lub szyfrowania wiadomości. Poniższy kod przedstawia sposób klasa wyprowadzona z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:  
  
```csharp  
public class MyCustomAlgorithmSuite : SecurityAlgorithmSuite  
    {  
        public override string DefaultAsymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaOaepKeyWrap; }  
        }  
  
        public override string DefaultAsymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaSha1Signature; }  
        }  
  
        public override string DefaultCanonicalizationAlgorithm  
        {  
            get { return SecurityAlgorithms.ExclusiveC14n; ; }  
        }  
  
        public override string DefaultDigestAlgorithm  
        {  
            get { return SecurityAlgorithms.MyCustomHashAlgorithm; }  
        }  
  
        public override string DefaultEncryptionAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override int DefaultEncryptionKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSignatureKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSymmetricKeyLength  
        {  
            get { return 128; }  
        }  
  
        public override string DefaultSymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override string DefaultSymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.HmacSha1Signature; }  
        }  
  
        public override bool IsAsymmetricKeyLengthSupported(int length)  
        {  
            return length >= 1024 && length <= 4096;  
        }  
  
        public override bool IsSymmetricKeyLengthSupported(int length)  
        {  
            return length >= 128 && length <= 256;  
        }  
    }  
```  
  
## <a name="register-the-custom-algorithm"></a>Rejestrowanie algorytmu niestandardowych  
 Rejestracja może odbywać się w pliku konfiguracji lub w kodzie nadrzędnych. Rejestrowanie niestandardowe algorytm należy utworzyć mapowanie między klasy, która implementuje dostawcę usług kryptograficznych i alias. Alias jest następnie mapowany do identyfikatora URI, który jest używany podczas określania algorytm w powiązaniu usługi WCF. Poniższy fragment konfiguracji przedstawia sposób rejestrowania niestandardowego algorytmu w konfiguracji:  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://constoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 W sekcji <`cryptoClasses`> elementu tworzy mapowanie między SHA256CryptoServiceProvider i alias "SHA256CSP". <`nameEntry`> Elementu tworzy mapowanie między alias "SHA256CSP" i określonego adresu URL (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm).  
  
 Aby zarejestrować niestandardowy algorytm używany kod <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm%2A> System.String[])?qualifyHint=False & autoUpgrade = True metody. Ta metoda tworzy oba mapowania. Poniższy przykład przedstawia sposób wywołania tej metody:  
  
```  
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a>Konfigurowanie powiązania  
 Skonfiguruj powiązanie, określając niestandardowy <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-pochodnej klasy w ustawieniach powiązanie, jak pokazano w poniższy fragment kodu:  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 Na przykład kompletny kod, zobacz [Zręczność kryptograficzna w zabezpieczeniach WCF](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) próbki.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Zabezpieczanie usług](../../../../docs/framework/wcf/securing-services.md)  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Pojęcia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md)
