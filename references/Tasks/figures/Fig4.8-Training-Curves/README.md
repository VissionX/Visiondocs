# Fig 4.8 — AbserneyVision training accuracy and loss curves
Export from your PyTorch training script using matplotlib:

  import matplotlib.pyplot as plt
  fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12, 4))
  ax1.plot(train_acc_p1, label='Train (Phase 1)')
  ax1.plot(val_acc_p1,   label='Val (Phase 1)')
  ax1.plot(train_acc_p2, label='Train (Phase 2)')
  ax1.plot(val_acc_p2,   label='Val (Phase 2)')
  ax1.set_title('Accuracy'); ax1.legend()
  ax2.plot(train_loss_p1); ax2.plot(val_loss_p1)
  ax2.plot(train_loss_p2); ax2.plot(val_loss_p2)
  ax2.set_title('Loss')
  plt.savefig('fig_4_8_training_curves.png', dpi=150, bbox_inches='tight')

Filename to use: fig_4_8_training_curves.png
