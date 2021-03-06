---
title: Azure リソースを別のリージョンに移動する
description: Azure リージョン間の Azure リソースの移動の概要について説明します。
author: rayne-wiselman
ms.service: azure-resource-manager
ms.topic: conceptual
ms.date: 11/21/2019
ms.author: raynew
ms.openlocfilehash: 22d8bcee96b4ac52641d4f0841267195f44fe15a
ms.sourcegitcommit: 2ec4b3d0bad7dc0071400c2a2264399e4fe34897
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "75476593"
---
# <a name="moving-azure-resources-across-regions"></a>リージョン間の Azure リソースの移動

この記事では、Azure リージョン間の Azure リソースの移動に関する情報を提供します。

Azure の地域、リージョン、および可用性ゾーンによって Azure グローバル インフラストラクチャの基礎が形成されます。 Azure の[地域](https://azure.microsoft.com/global-infrastructure/geographies/)には通常、2 つ以上の [Azure リージョン](https://azure.microsoft.com/global-infrastructure/regions/)が含まれます。 リージョンとは、可用性ゾーンや複数のデータ センターが含まれている、地域内のある領域のことです。 

特定の Azure リージョンにリソースをデプロイした後、それらのリソースを別のリージョンに移動したくなる理由がいくつか存在します。

- **リージョンの立ち上げに合わせる**: 以前には使用できなかった、新しく導入された Azure リージョンにリソースを移動します。
- **サービス/機能に合わせる**: 特定のリージョンで使用可能になったサービスまたは機能を利用するためにリソースを移動します。
- **ビジネスの展開に対応する**: 合併や買収などのビジネスの変化に対応して、あるリージョンにリソースを移動します。
- **距離の近さに合わせる**: ビジネスの近くに存在するリージョンにリソースを移動します。
- **データの要件を満たす**: データ所在地の要件やデータ分類のニーズに合わせるためにリソースを移動します。 [詳細については、こちらを参照してください](https://azure.microsoft.com/mediahandler/files/resourcefiles/achieving-compliant-data-residency-and-security-with-azure/Achieving_Compliant_Data_Residency_and_Security_with_Azure.pdf)。
- **デプロイ要件に対応する**: デプロイ時にエラーが発生したリソースを移動するか、または容量のニーズに対応して移動します。 
- **使用停止に対応する**: リージョンの使用停止のためにリソースを移動します。

## <a name="move-process"></a>移動プロセス

実際の移動プロセスは、移動しているリソースによって異なります。 ただし、一般的な重要な手順がいくつか存在します。

- **前提条件を確認する**: 前提条件には、必要なリソースがターゲット リージョンで使用できることの確認、十分なクォータがあることの確認、およびサブスクリプションがターゲット リージョンにアクセスできることの確認が含まれます。
- **依存関係を分析する**: あるリソースが他のリソースに依存していることがあります。 移動する前に、移動されたリソースが移動後も引き続き想定どおりに機能するように依存関係を見つけてください。
- **移動に対して準備する**: これは、移動の前にプライマリ リージョンで実行する手順です。 たとえば、Azure Resource Manager テンプレートをエクスポートしたり、ソースからターゲットへのリソースのレプリケーションを開始したりすることが必要になる場合があります。
- **リソースを移動する**: リソースを移動する方法は、それがどのようなリソースであるかによって異なります。 テンプレートをターゲット リージョンにデプロイしたり、リソースをターゲットにフェールオーバーしたりすることが必要になる場合があります。
- **ターゲット リソースを破棄する**: リソースを移動した後、ターゲット リージョンに移動されたリソースを調べ、不要なものが存在しないかどうかを判定することが必要になる場合があります。
- **移動をコミットする**: ターゲット リージョンのリソースを確認した後、一部のリソースに最終的なコミット アクションが必要になる場合があります。 たとえば、プライマリ リージョンになったターゲット リージョンでは、新しいセカンダリ リージョンへのディザスター リカバリーを設定することが必要になる場合があります。 
- **ソースをクリーンアップする**: 最後に、すべてが新しいリージョンで稼働状態になったら、移動のために作成したリソースやプライマリ リージョン内のリソースをクリーンアップし、使用を停止することができます。



## <a name="next-steps"></a>次のステップ

リージョン間の移動がサポートされているリソースの一覧については、[リソースの移動操作のサポート](region-move-support.md)に関するページを参照してください。
