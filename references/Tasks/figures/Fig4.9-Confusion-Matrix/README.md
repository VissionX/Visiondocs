# Fig 4.9 — Confusion matrix (AbserneyVision validation)
Export from model evaluation:

  from sklearn.metrics import ConfusionMatrixDisplay
  import matplotlib.pyplot as plt
  disp = ConfusionMatrixDisplay(confusion_matrix=cm, display_labels=CLASS_NAMES)
  fig, ax = plt.subplots(figsize=(10, 10))
  disp.plot(ax=ax, colorbar=False, cmap='Blues')
  plt.title('AbserneyVision — Confusion Matrix (Val Set)')
  plt.savefig('fig_4_9_confusion_matrix.png', dpi=150, bbox_inches='tight')

Filename to use: fig_4_9_confusion_matrix.png
