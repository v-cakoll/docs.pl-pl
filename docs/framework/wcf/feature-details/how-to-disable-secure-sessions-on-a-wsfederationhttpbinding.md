---
title: 'Instrukcje: Wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 97fc358ac66bb92ccc40c92207bf6561f61b84f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489879"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a>Instrukcje: Wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding
Niektóre usługi mogą wymagają poświadczeń federacyjnych, ale nie obsługują bezpiecznej sesji. W takim przypadku należy wyłączyć funkcję bezpiecznej sesji. W odróżnieniu od <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, <xref:System.ServiceModel.WSFederationHttpBinding> klasa nie zapewnia możliwość wyłączenia bezpiecznej sesji podczas komunikacji z usługą. Zamiast tego należy utworzyć niestandardowego powiązania, który zastępuje ładowania początkowego ustawienia bezpiecznej sesji.  
  
 W tym temacie przedstawiono sposób modyfikowania elementów wiązania zawartych w <xref:System.ServiceModel.WSFederationHttpBinding> do tworzenia niestandardowego powiązania. Wynik jest taki sam jak <xref:System.ServiceModel.WSFederationHttpBinding> z tą różnicą, że nie używa bezpiecznych sesji.  
  
### <a name="to-create-a-custom-federated-binding-without-secure-session"></a>Aby utworzyć niestandardowy federacyjnych powiązania bez bezpiecznej sesji  
  
1.  Utwórz wystąpienie <xref:System.ServiceModel.WSFederationHttpBinding> klasy imperatively w kodzie lub przez załadowanie go z pliku konfiguracji.  
  
2.  Klonowanie <xref:System.ServiceModel.WSFederationHttpBinding> do <xref:System.ServiceModel.Channels.CustomBinding>.  
  
3.  Znajdź <xref:System.ServiceModel.Channels.SecurityBindingElement> w <xref:System.ServiceModel.Channels.CustomBinding>.  
  
4.  Znajdź <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> w <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
5.  Zastąp oryginalny <xref:System.ServiceModel.Channels.SecurityBindingElement> z elementu powiązania zabezpieczeń ładowania początkowego z <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy niestandardowego powiązania federacyjnego bez bezpiecznej sesji.  
  
 [!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
 [!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Aby skompilować przykładów kodu, należy utworzyć projekt, który odwołuje się do zestawu System.ServiceModel.dll.  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązania i zabezpieczenia](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
