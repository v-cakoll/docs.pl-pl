---
title: Mapowanie nazw algorytmów na klasy kryptografii
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: 6ec98aabd92a7a0fed11482bdf6e5e8ddc045a7e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098744"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>Mapowanie nazw algorytmów na klasy kryptografii
Istnieją cztery sposoby Deweloper można utworzyć obiektu kryptografii przy użyciu [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:  
  
-   Utwórz obiekt przy użyciu **nowe** operatora.  
  
-   Utwórz wystąpienie obiektu implementującego na algorytm kryptograficzny określonego przez wywołanie metody **Utwórz** metody abstrakcyjne klasy dla tego algorytmu.  
  
-   Utwórz wystąpienie obiektu implementującego na algorytm kryptograficzny określonego przez wywołanie metody <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody.  
  
-   Utwórz obiekt, który implementuje klasa algorytmów kryptograficznych (takich jak symetrycznym szyfrem) przez wywołanie metody **Utwórz** metody abstrakcyjne klasy dla tego typu algorytmu (takie jak <xref:System.Security.Cryptography.SymmetricAlgorithm>).  
  
 Na przykład załóżmy, że deweloper chce obliczenia skrótu SHA1 zestawu bajtów. <xref:System.Security.Cryptography> Przestrzeń nazw zawiera dwie implementacje algorytmu SHA1, co czysto zarządzaną implementację i jedną, która opakowuje interfejs CryptoAPI. Deweloper można wybrać do utworzenia wystąpienia określonej implementacji SHA1 (takie jak <xref:System.Security.Cryptography.SHA1Managed>) przez wywołanie metody **nowe** operatora. Jednak jeśli nie ma znaczenia, klasa, która ładuje środowisko uruchomieniowe języka wspólnego, tak długo, jak klasa implementuje algorytm wyznaczania wartości skrótu SHA1, deweloper można utworzyć obiektu przez wywołanie metody <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> metody. Ta metoda wywołuje **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, który musi zwrócić implementację algorytmu wyznaczania wartości skrótu SHA1.  
  
 Deweloper można również wywołać **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** ponieważ domyślnie kryptografii Konfiguracja obejmuje krótkich nazw dla algorytmów dostarczane w programie .NET Framework.  
  
 Jeśli jest używany algorytm wyznaczania wartości skrótu, który nie ma znaczenia, deweloper może wywołać <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> metody, która zwraca obiekt, który implementuje przekształcania wyznaczania wartości skrótu.  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>Mapowanie nazw algorytmów w plikach konfiguracji  
 Domyślnie środowisko wykonawcze zwraca <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> obiektu dla wszystkich, cztery scenariusze. Jednak administrator komputera można zmienić typu obiektu, zwracane metod w ostatnich dwóch scenariuszy. Aby to zrobić, należy zamapować algorytm przyjazną nazwę klasy, których chcesz użyć w pliku konfiguracji komputera (Machine.config).  
  
 Poniższy przykład przedstawia sposób konfigurowania środowiska uruchomieniowego, aby **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, i  **System.Security.Cryptography.HashAlgorithm.Create** zwracają `MySHA1HashClass` obiektu.  
  
```xml  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 Możesz określić nazwę atrybutu w [< cryptoclass —\> elementu](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (poprzedni przykład nazwy atrybutu `MySHA1Hash`). Wartość atrybutu w  **\<cryptoclass — >** element stanowi ciąg, który używa środowiska uruchomieniowego języka wspólnego, można znaleźć klasy. Można użyć dowolnego ciągu, który spełnia wymagania określone w [określanie w pełni kwalifikowanej nazwy typu](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).  
  
 Wiele nazw algorytm można mapować do tej samej klasy. [ \<Nameentry — > element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) mapuje klasy jeden algorytm przyjazną nazwę. **Nazwa** atrybut może być ciąg, który jest używany podczas wywoływania **System.Security.Cryptography.CryptoConfig.CreateFromName** metody lub nazwę klasy abstrakcyjnej kryptografii w <xref:System.Security.Cryptography> przestrzeni nazw. Wartość **klasy** atrybut jest nazwą atrybutu w  **\<cryptoclass — >** elementu.  
  
> [!NOTE]
>  Algorytm SHA1 można uzyskać przez wywołanie metody <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> lub **Security.CryptoConfig.CreateFromName("SHA1")** metody. Każda metoda gwarantuje tylko zwraca obiekt, który implementuje algorytm SHA1. Nie masz mapowania każdego przyjazna nazwa algorytmu do tej samej klasy w pliku konfiguracji.  
  
 Aby uzyskać listę domyślnych nazw i klas mapowania ich na, zobacz <xref:System.Security.Cryptography.CryptoConfig>.  
  
## <a name="see-also"></a>Zobacz także

- [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)
- [Konfigurowanie klas kryptografii](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
