---
title: Określanie niestandardowego algorytmu kryptograficznego
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: c92ce463f885e9784913b07eb11941ecd7d78d09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113714"
---
# <a name="specifying-a-custom-crypto-algorithm"></a>Określanie niestandardowego algorytmu kryptograficznego
WCF umożliwia określanie niestandardowego algorytmu kryptograficznego do użycia podczas szyfrowania danych lub przetwarzania podpisów cyfrowych. Jest to realizowane przez następujące kroki:  
  
1.  Wyprowadzić klasę z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>  
  
2.  Rejestrowanie algorytmu  
  
3.  Konfigurowanie powiązania z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-klasy pochodnej.  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a>Wyprowadzenia klasy z SecurityAlgorithmSuite  
 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> Jest abstrakcyjną klasę bazową, która pozwala na Określanie algorytmu do użycia podczas przeprowadzania zabezpieczeń różnych operacji związanych z. Na przykład obliczanie skrótu do podpisu cyfrowego lub szyfrowania wiadomości. Poniższy kod przedstawia sposób wyprowadzić klasę z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:  
  
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
  
## <a name="register-the-custom-algorithm"></a>Rejestrowanie niestandardowego algorytmu  
 Rejestracja może odbywać się w pliku konfiguracji lub kodu imperatywnego. Rejestrowanie niestandardowego algorytmu odbywa się przez utworzenie mapowanie między klasę, która implementuje dostawcę usług kryptograficznych i alias. Alias jest następnie mapowany do identyfikatora URI, który jest używany podczas określania algorytm w powiązaniu usługi WCF. Poniższy fragment kodu konfiguracji przedstawia sposób rejestrowania niestandardowego algorytmu w konfiguracji:  
  
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
  
 W sekcji <`cryptoClasses`> element tworzy mapowanie między SHA256CryptoServiceProvider i alias "SHA256CSP". <`nameEntry`> Element tworzy mapowanie między aliasu "SHA256CSP" i pod określony adres URL (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).  
  
 Do rejestrowania niestandardowego algorytmu używany kod <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> metody. Ta metoda tworzy oba mapowania. Poniższy przykład pokazuje, jak wywołać tę metodę:  
  
```  
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a>Konfigurowanie powiązania  
 Konfigurowanie powiązania, określając niestandardowy <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-pochodne klasy w ustawieniach powiązania, jak pokazano w poniższym fragmencie kodu:  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 Aby uzyskać pełny przykład kodu, zobacz [Zręczność kryptograficzna w zabezpieczeniach WCF](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) próbki.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Zabezpieczanie usług](../../../../docs/framework/wcf/securing-services.md)
- [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Pojęcia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md)
