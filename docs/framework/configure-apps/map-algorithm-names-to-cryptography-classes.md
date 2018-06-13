---
title: Mapowanie nazw algorytmów na klasy kryptografii
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2dc03c3aa6808ed4ce0c22f4e69fa8c98cb7aebd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758259"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>Mapowanie nazw algorytmów na klasy kryptografii
Istnieją cztery metody dewelopera można utworzyć obiektu kryptografii przy użyciu [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:  
  
-   Tworzenie obiektu przy użyciu **nowe** operatora.  
  
-   Utwórz obiekt, który implementuje algorytmu szyfrowania określonego przez wywołanie metody **Utwórz** metody w abstrakcyjnej klasie dla tego algorytmu.  
  
-   Utwórz obiekt, który implementuje algorytmu szyfrowania określonego przez wywołanie metody <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody.  
  
-   Utwórz obiekt, który implementuje klasy algorytmów kryptograficznych (takich jak symetrycznym szyfrem) przez wywołanie metody **Utwórz** metody w abstrakcyjnej klasie dla tego typu algorytmu (takie jak <xref:System.Security.Cryptography.SymmetricAlgorithm>).  
  
 Na przykład załóżmy, że deweloper chce obliczeniowe skrótu SHA1 zestawu bajtów. <xref:System.Security.Cryptography> Przestrzeń nazw zawiera dwa implementacje algorytmu SHA1, jedna implementacja wyłącznie zarządzany i który opakowuje interfejsu CryptoAPI. Deweloper można wybrać do utworzenia wystąpienia określonej implementacji SHA1 (takich jak <xref:System.Security.Cryptography.SHA1Managed>) przez wywołanie metody **nowe** operatora. Jednak jeśli nie ma znaczenia, która klasa środowisko uruchomieniowe języka wspólnego ładuje tak długo, jak klasa implementuje algorytmu wyznaczania wartości skrótu SHA1, deweloper może utworzyć obiektu przez wywołanie metody <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> metody. Ta metoda wywołuje **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, który musi zwracać implementację algorytmu wyznaczania wartości skrótu SHA1.  
  
 Deweloper może także wywołać **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** ponieważ domyślnie kryptografii konfiguracji zawiera krótkie nazwy algorytmów wysłane w programie .NET Framework.  
  
 Jeśli nie ma znaczenia, który algorytm wyznaczania wartości skrótu jest używany, deweloper może wywołać <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> metody, która zwraca obiekt, który implementuje transformację wyznaczania wartości skrótu.  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>Mapowanie nazw algorytmu w plikach konfiguracji  
 Domyślnie środowisko uruchomieniowe zwraca <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> obiektu we wszystkich scenariuszach cztery. Jednak administrator maszyny można zmienić typu obiektu, który zwraca metod w ostatnie dwa scenariusze. W tym celu zamapuj algorytm przyjazną nazwę klasy, które mają być używane w pliku konfiguracji komputera (Machine.config).  
  
 Poniższy przykład przedstawia sposób konfigurowania środowiska uruchomieniowego, aby **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, i  **System.Security.Cryptography.HashAlgorithm.Create** zwracać `MySHA1HashClass` obiektu.  
  
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
  
 Można określić nazwę atrybutu w [< cryptoclass —\> elementu](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (poprzedni przykład nazwy atrybutu `MySHA1Hash`). Wartość atrybutu w  **\<cryptoclass — >** element jest ciągiem, który używa środowiska CLR można znaleźć klasy. Można użyć dowolnego ciągu, który spełnia wymagania określone w [określenie pełni kwalifikowane nazwy typów](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).  
  
 Wiele nazw algorytm można mapować do tej samej klasy. [ \<Nameentry — > element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) mapuje jedną algorytm przyjazną nazwę klasy. **Nazwa** atrybut może być ciągiem, który jest używany podczas wywoływania metody **System.Security.Cryptography.CryptoConfig.CreateFromName** metody lub nazwę klasy abstrakcyjnej kryptografii w <xref:System.Security.Cryptography> przestrzeni nazw. Wartość **klasy** atrybut jest nazwą atrybutu w  **\<cryptoclass — >** elementu.  
  
> [!NOTE]
>  Algorytm SHA1 można uzyskać przez wywołanie metody <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> lub **Security.CryptoConfig.CreateFromName("SHA1")** metody. Każda metoda gwarantuje tylko zwraca obiekt, który implementuje algorytmu SHA1. Nie masz mapowania każdego przyjazną nazwę algorytmu do tej samej klasy w pliku konfiguracji.  
  
 Aby uzyskać listę domyślnych nazw i klas, są one wykonywane na zobacz <xref:System.Security.Cryptography.CryptoConfig>.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)  
 [Konfigurowanie klas kryptografii](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
