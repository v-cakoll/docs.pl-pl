---
title: 'Instrukcje: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
ms.openlocfilehash: 810c5b127a34fb0a35e8fd2d83ff59e00aca0ba1
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972046"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a>Instrukcje: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding

Niektóre usługi mogą wymagać poświadczeń federacyjnych, ale nie obsługują bezpiecznych sesji. W takim przypadku należy wyłączyć funkcję bezpiecznej sesji. W przeciwieństwie <xref:System.ServiceModel.WSHttpBinding>do <xref:System.ServiceModel.WSFederationHttpBinding> klasy, Klasa nie pozwala na wyłączenie bezpiecznych sesji podczas komunikacji z usługą. Zamiast tego należy utworzyć niestandardowe powiązanie, które zastępuje ustawienia bezpiecznej sesji przy użyciu Bootstrap.

W tym temacie pokazano, jak modyfikować elementy powiązania zawarte w elemencie <xref:System.ServiceModel.WSFederationHttpBinding> w celu utworzenia niestandardowego powiązania. Wynik jest identyczny <xref:System.ServiceModel.WSFederationHttpBinding> z tą różnicą, że nie używa bezpiecznych sesji.

## <a name="to-create-a-custom-federated-binding-without-secure-session"></a>Aby utworzyć niestandardowe powiązanie federacyjne bez bezpiecznej sesji

1. Utwórz wystąpienie <xref:System.ServiceModel.WSFederationHttpBinding> klasy jako bezwzględnie w kodzie lub przez załadowanie jednego z pliku konfiguracji.

2. Klonowanie<xref:System.ServiceModel.Channels.CustomBinding>do <xref:System.ServiceModel.WSFederationHttpBinding> .

3. <xref:System.ServiceModel.Channels.SecurityBindingElement> Znajdź<xref:System.ServiceModel.Channels.CustomBinding>w.

4. <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> Znajdź<xref:System.ServiceModel.Channels.SecurityBindingElement>w.

5. Zastąp oryginał <xref:System.ServiceModel.Channels.SecurityBindingElement> elementem powiązania zabezpieczeń Bootstrap <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>z.

## <a name="example"></a>Przykład

Poniższy przykład powoduje utworzenie niestandardowego powiązania federacyjnego bez bezpiecznej sesji.

[!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
[!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

- Aby skompilować przykład kodu, Utwórz projekt, który odwołuje się do zestawu System. ServiceModel. dll.

## <a name="see-also"></a>Zobacz także

- [Powiązania i zabezpieczenia](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
