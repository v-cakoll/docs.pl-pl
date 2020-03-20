---
title: Określanie niestandardowego algorytmu kryptograficznego
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: 673d177a665e265d77f0221e0a00f4b814c8795c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186486"
---
# <a name="specifying-a-custom-crypto-algorithm"></a>Określanie niestandardowego algorytmu kryptograficznego
WCF umożliwia określenie niestandardowego algorytmu kryptograficznego używanego podczas szyfrowania danych lub przetwarzania podpisów cyfrowych. Odbywa się to w następujących krokach:  
  
1. Wyprowadz klasę z<xref:System.ServiceModel.Security.SecurityAlgorithmSuite>  
  
2. Zarejestruj algorytm  
  
3. Skonfiguruj <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>powiązanie z klasą pochodną.  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a>Czerpanie klasy z SecurityAlgorithmSuite  
 Jest <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> abstrakcyjną klasą podstawową, która umożliwia określenie algorytmu do użycia podczas wykonywania różnych operacji związanych z zabezpieczeniami. Na przykład obliczanie skrótu dla podpisu cyfrowego lub szyfrowanie wiadomości. Poniższy kod pokazuje, jak wyprowadzić klasę z: <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>  
  
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
  
## <a name="register-the-custom-algorithm"></a>Zarejestruj algorytm niestandardowy  
 Rejestracja może odbywać się w pliku konfiguracyjnym lub w kodzie imperatywnym. Rejestrowanie niestandardowego algorytmu odbywa się przez utworzenie mapowania między klasą, która implementuje dostawcę usług kryptograficznych i alias. Alias jest następnie mapowane do identyfikatora URI, który jest używany podczas określania algorytmu w powiązanie usługi WCF. Poniższy fragment kodu konfiguracji ilustruje sposób rejestrowania niestandardowego algorytmu w konfiguracji:  
  
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
  
 Sekcja w <`cryptoClasses`> element tworzy mapowanie między SHA256CryptoServiceProvider i alias "SHA256CSP". Element <`nameEntry`> tworzy mapowanie między aliasem "SHA256CSP" a określonym `http://constoso.com/CustomAlgorithms/CustomHashAlgorithm`adresem URL .  
  
 Aby zarejestrować niestandardowy algorytm <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> w kodzie należy użyć metody. Ta metoda tworzy oba mapowania. W poniższym przykładzie pokazano, jak wywołać tę metodę:  
  
```csharp
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a>Konfigurowanie powiązania  
 Powiązanie można skonfigurować, określając <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>niestandardową klasę pochodną w ustawieniach powiązania, jak pokazano w poniższym fragmentie kodu:  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 Aby uzyskać przykład pełnego kodu, zobacz [kryptograficzne agility w WCF security](../samples/cryptographic-agility-in-wcf-security.md) próbki.  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczanie usług i klientów](../feature-details/securing-services-and-clients.md)
- [Zabezpieczanie usług](../securing-services.md)
- [Omówienie zabezpieczeń](../feature-details/security-overview.md)
- [Pojęcia dotyczące zabezpieczeń](../feature-details/security-concepts.md)
