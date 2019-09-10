---
title: Określanie niestandardowego algorytmu kryptograficznego
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: 55200732b392c15a25853af28ecdf9e32d092da4
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849106"
---
# <a name="specifying-a-custom-crypto-algorithm"></a>Określanie niestandardowego algorytmu kryptograficznego
Usługa WCF umożliwia określenie niestandardowego algorytmu kryptograficznego, który ma być używany podczas szyfrowania danych lub przetwarzania podpisów cyfrowych. W tym celu należy wykonać następujące czynności:  
  
1. Utwórz klasę z<xref:System.ServiceModel.Security.SecurityAlgorithmSuite>  
  
2. Rejestrowanie algorytmu  
  
3. Skonfiguruj powiązanie z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>klasą pochodną.  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a>Utwórz klasę z SecurityAlgorithmSuite  
 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> Jest abstrakcyjną klasą bazową, która pozwala określić algorytm, który ma być używany podczas wykonywania różnych operacji związanych z zabezpieczeniami. Na przykład Obliczanie skrótu podpisu cyfrowego lub szyfrowanie wiadomości. Poniższy kod przedstawia sposób wygenerowania klasy z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:  
  
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
 Rejestrację można przeprowadzić w pliku konfiguracji lub w bezwzględnym kodzie. Zarejestrowanie algorytmu niestandardowego odbywa się przez utworzenie mapowania między klasą, która implementuje dostawcę usług kryptograficznych i alias. Alias jest następnie mapowany na identyfikator URI, który jest używany podczas określania algorytmu w powiązaniu usługi WCF. Poniższy fragment konfiguracji ilustruje sposób rejestrowania niestandardowego algorytmu w konfiguracji:  
  
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
  
 Sekcja w <`cryptoClasses`elementu > tworzy mapowanie między SHA256CryptoServiceProvider i aliasem "SHA256CSP". <`nameEntry`Element > tworzy mapowanie między aliasem "SHA256CSP" i określonym adresem URL (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).  
  
 Aby zarejestrować niestandardowy algorytm w kodzie, <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> Użyj metody. Ta metoda powoduje utworzenie obu mapowań. Poniższy przykład pokazuje, jak wywołać tę metodę:  
  
```csharp
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a>Konfigurowanie powiązania  
 Powiązanie można skonfigurować przez określenie klasy pochodnej niestandardowej <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>w ustawieniach powiązań, jak pokazano w poniższym fragmencie kodu:  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 Aby uzyskać kompletny przykład kodu, zobacz [elastyczność kryptograficzną w przykładowym zabezpieczeniu WCF](../samples/cryptographic-agility-in-wcf-security.md) .  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie usług i klientów](../feature-details/securing-services-and-clients.md)
- [Zabezpieczanie usług](../securing-services.md)
- [Przegląd zabezpieczeń](../feature-details/security-overview.md)
- [Pojęcia dotyczące zabezpieczeń](../feature-details/security-concepts.md)
